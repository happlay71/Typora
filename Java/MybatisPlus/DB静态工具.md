### *Cotroller层*

#### 查询单个用户id

```java
	@ApiOperation("根据id查询用户接口")
    @GetMapping("{id}")
    public UserVO queryUserById(@ApiParam("用户id") @PathVariable("id") Long id) {
        return userService.queryUsersAndAddressById(id);
    }
```

#### 批量查询用户id

```java
	@ApiOperation("根据id批量查询用户接口")
    @GetMapping
    public List<UserVO> queryUserByIds(@ApiParam("用户id集合") @RequestParam("ids") List<Long> ids) {
//        List<User> users = userService.listByIds(ids);
//        // 拷贝成VO
//        return BeanUtil.copyToList(users, UserVO.class);
        return userService.queryUsersAndAddressByIds(ids);
    }
```

### IUserService层

```java
UserVO queryUsersAndAddressById(Long id);
```

```java
List<UserVO> queryUsersAndAddressByIds(List<Long> ids);
```

### IUserServiceImpl层

#### 查询单个用户id

```java
	@Override
    public UserVO queryUsersAndAddressById(Long id) {
        // 1.查询用户
        User user = getById(id);
        if (user == null || user.getStatus() == 2) {
            throw new RuntimeException("用户状态异常");
        }
        // 2.查询地址
        // 静态方法Db
        List<Address> addresses = Db.lambdaQuery(Address.class)
                .eq(Address::getUserId, id)
                .list();
        // 3.封装VO
        // 3.1 将一个名为user的对象转换为UserVO对象
        UserVO userVO = BeanUtil.copyProperties(user, UserVO.class);
        // 3.2 转地址VO
        // CollUtil-工具类，提供了各种对集合操作的方法
        if (CollUtil.isNotEmpty(addresses)) {
            userVO.setAddresses(BeanUtil.copyToList(addresses, AddressVO.class));
        }
        return userVO;
    }
```

#### 批量查询用户id

```java
	@Override
    public List<UserVO> queryUsersAndAddressByIds(List<Long> ids) {
        // 1.查询用户
        List<User> users = listByIds(ids);
        if (CollUtil.isEmpty(users)) {
            return Collections.emptyList();  // 返回空集合
        }
        // 2.查询地址
        // 2.1 使用stream流收集user_id
        List<Long> userIds = users.stream().map(User::getId).collect(Collectors.toList());
        // 2.2 根据用户id查询地址
        List<Address> addresses = Db.lambdaQuery(Address.class)
                .in(Address::getUserId, userIds)
                .list();
        // 2.3 转VO
        List<AddressVO> addressVOList = BeanUtil.copyToList(addresses, AddressVO.class);
        // 2.4 用户地址集合分组处理，相同用户id在一个组里
        Map<Long, List<AddressVO>> addressMap = new HashMap<>(0);
        if (CollUtil.isNotEmpty(addressVOList)) {
            addressMap = addressVOList.stream().collect(Collectors.groupingBy(AddressVO::getUserId));
        }

        // 3.封装VO
        List<UserVO> list = new ArrayList<>(users.size());
        for (User user : users) {
            // 3.1 转User的Po为Vo
            UserVO userVO = BeanUtil.copyProperties(user, UserVO.class);
            list.add(userVO);
            // 3.2 在addresses里找到对应userVO的地址
            userVO.setAddresses(addressMap.get(userVO.getId()));
        }

        return list;
    }
```

