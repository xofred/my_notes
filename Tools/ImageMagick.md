Recently, my day job requires me to fetch posters from APIs provided by an ally. Question is, ally posters' resolution do not fit ours. So here, ImageMagick comes in very handy.

**original**

![original](http://thumbnail0.baidupcs.com/thumbnail/3871b9b0c74dbc4d0268bae5b007886e?fid=3210612086-250528-180300931270327&time=1461549600&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-LNpTxWhx188UsqDzP7%2Bidc1egPo%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=2677303667911356093&dp-callid=0&size=c710_u400&quality=100)

**background**

![background](http://thumbnail0.baidupcs.com/thumbnail/3582b8d2347e5329e6afbd18ec1355fe?fid=3210612086-250528-518663358185165&time=1461549600&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-u1%2BmRV0%2FjBUOfCcLasHvbTw%2FRoQ%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=2677317484619827448&dp-callid=0&size=c710_u400&quality=100)

**composite**

![composite](http://thumbnail0.baidupcs.com/thumbnail/55d69f93cbe6013868cd72042ea4c4de?fid=3210612086-250528-902517305469107&time=1461549600&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-enb34GKO5Pk5YQxwuNU6GffMEvI%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=2677290182042921859&dp-callid=0&size=c710_u400&quality=100)

**code**

```ruby
    def convert_image(show_id, url)
      image = MiniMagick::Image.open(url) # which will create a duplicated
      MiniMagick::Tool::Convert.new do |convert| # background image
        convert << image.path
        convert.merge! ["-resize", "720x405^", "-gravity", "center", "-extent", "720x405", "-gaussian-blur", "60x20"]
        convert << Rails.root.join("tmp/background#{show_id}.jpg")
      end
      background = MiniMagick::Image.open(Rails.root.join("tmp/background#{show_id}.jpg"))
      result = background.composite(image) do |c| # composite
        c.gravity "center"
      end
      result.write Rails.root.join("tmp/output#{show_id}.jpg")
      Show.find(show_id).update!(poster: File.open(Rails.root.join("tmp/output#{show_id}.jpg"))) # carrierwave 'upload' a loacal file
    end
```

Reference: 

- [ImageMagick v6 Examples -- 
 Resize or Scaling (General Techniques)](http://www.imagemagick.org/Usage/resize/)

- [minimagick/minimagick: mini replacement for RMagick](https://github.com/minimagick/minimagick)

