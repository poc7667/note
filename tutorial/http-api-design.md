# http api design

---

+ 每个实体对应一个 url，url 中使用名词，不要包含动作。
+ 使用 http method 来表示对实体进行某种操作。
    - `PUT` 增
    - `DELETE` 删
    - `POST` 改
    - `GET` 查
+ 复杂修改的时候，使用 url 明确表明这是某种修改
    - `/resource/:id/action/:act`

---

+ 对于部分没有实体的请求，url 中使用动词。
    - `/convert?from=EUR&to=CNY&amount=100`

---

+ 发生错误时，返回 200，在返回值中给出错误信息。
+ 唯一的 `error_code` 配合完整的说明文档。
+ 在 `error_code` 不够用的时候，在 data 中放需要的额外信息。
+ 有错时，`error_code` 为真值，方便判断。

```json
{
    error: [0 | error_code],
    data: [NULL | error_data]
}
```

---

+ 在 url 中给出具体的版本信息。
    - `/api/v1/blah`
    - `/api/v2/blah`

---

+ 使用 `fields` 来精简返回值。
    - `?fields=id,title,author`
+ 如果需要进行更复杂的筛选，感觉不好表达。
    - `?fields=article:(title,date,author:(id,name))`
    - `?fields=article.title,article.date,article.author.id,article.author.name`

---

+ 使用 `limit` 和 `offset` 来翻页。
    - `?limit=10&offset=0`

---

+ 使用 `q` 进行关键字搜索。
    - `?q=blah+blah`

---

+ 允许使用 `method` 来指定 http method
    - `?method=delete`

---

+ 使用 OAuth2.0 进行身份认证

---

## reference

+ https://pages.apigee.com/web-api-design-ebook.html
+ https://github.com/interagent/http-api-design/tree/master
