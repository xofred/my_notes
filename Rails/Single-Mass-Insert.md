```ruby
        inserts = []
        timenow = Time.now.strftime('%Y-%m-%d %H:%M:%S')
        show_id = show.id
        area_id = area.id
        rest_tickets.times do
          #show.seats.where(area_id: area.id).create(status: Ticket::seat_types[:avaliable], price: price)
          inserts.push "(#{show_id}, #{area_id}, 0, #{price}, '#{timenow}', '#{timenow}')"
        end
        sql = "INSERT INTO tickets (show_id, area_id, status, price, created_at, updated_at) VALUES #{inserts.join(', ')}"
        ActiveRecord::Base.connection.execute sql

```
Reference: [Mass inserting data in Rails without killing your performance](https://www.coffeepowered.net/2009/01/23/mass-inserting-data-in-rails-without-killing-your-performance/)