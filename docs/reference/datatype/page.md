## Page

Page数据类型用于翻页查询数据，用户每次查询可以只返回某一页的数据，列表页数据类型定义如下：  

| 名称             | 类型    | 描述                                                 |
| ---------------- | ------- | ---------------------------------------------------- |
| content          | []      | 具体的查询数据内容，数组内的数据随查询内容不同而不同 |
| totalPages       | int     | 被查询的数据总页数                                   |
| first            | boolean | 是否是第一页                                         |
| last             | boolean | 是否是最后一页                                       |
| totalElements    | int     | 被查询的数据总数                                     |
| number           | int     | 当前查询的页数，页数从0开始                          |
| size             | int     | 每页查询数据个数                                     |
| numberOfElements | int     | content中的数据数量                                  |

## 示例

参见[用户列表页示例](../../user/userpage#_7)

