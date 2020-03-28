
## 基础数据模型

### 系统
（通用）
- sys_app 应用系统，关联前端应用和oauth认证
- sys_service 后台服务，集成微服务的服务发现

### 用户
- sys_user 用户
- user_connect 第三方用户认证

如何区分内部用户、合作伙伴用户、2B客户的用户、2C用户

### 系统权限
（通用）
- sys_role 角色
- sys_perm 权限

### 菜单/按钮
（基于系统）
- sys_menu 权限-菜单

### 组织
（通用）
- sys_group 组  1=role,2=org,3=other
- sys_org 组织(树状)
- sys_positon = sys_org+sys_role


## 认证token

- token信息
  - 时间
    - 签发时间
    - 失效时间
  - 信息
    - 应用
    - 用户
    - 角色
  - 签名
