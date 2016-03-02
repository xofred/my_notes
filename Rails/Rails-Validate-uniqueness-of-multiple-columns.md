Let's say we have a City model, it has a name and a source fields. And we want city from the same source to has unique city name. Here's how we do.


`validates :name, presence: { message: "城市名字不能为空" }, uniqueness: { scope: :source, message: "城市名字不能重复" }`

Reference: [http://stackoverflow.com/questions/4870961/rails-validate-uniqueness-of-multiple-columns](http://stackoverflow.com/questions/4870961/rails-validate-uniqueness-of-multiple-columns)


