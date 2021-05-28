## Concerns
Rails includes [Active Support’s Concerns](https://goodscary.us1.list-manage.com/track/click?u=8978f575757c4b55d2a353a62&id=01476e0722&e=d9063823d8) as a way to group functionality that’s used in multiple places. It’s a wrapper around a standard Ruby `module`.

### `app/models/concerns/orderable_by_timestamp.rb`

```ruby
module OrderableByTimestamp
  extend ActiveSupport::Concern

  included do
    scope :by_earliest_created, -> { order(created_at: :asc) }
    scope :by_recently_created, -> { order(created_at: :desc) }
    scope :by_earliest_updated, -> { order(updated_at: :asc) }
    scope :by_recently_updated, -> { order(updated_at: :desc) }
  end
end
```

### `app/models/book.rb`

```ruby
class Book < ApplicationRecord
  include OrderableByTimestamp
end
```

This module could also be included in other models and provide the same functionality

Concers should be small so that when included into models do not overburden them with unnecessery methods
Use with coution

## Counter Cache
*As the name sugests* it's a cache for counters ( like in `User.articules.count`) it's stroes a value of count to fastend up counting proces. In **Rails** you can make a simple counter cache by adding, aproparate notation to belongs_to association nad by adding proper column i DB exp:
```ruby
class Comment
  belongs_to :article, counter_cache: true
end
```
This requires a field to the `Article` model named `comments_count`.
Whenever comment is added or removed value in comments_count will be updated
The field name can be overridden by using a symbol instead of `true` as the value for the `counter_cache` option.
In that situation Rails will new to use cunter cashe and do not make N+1 in case:
```ruby
articles.each do |article|
  article.title
  article.description 
  article.comments.size # use cunter_cashe
end
```
To  set proper counters one need to set them on relations that were creted before added counter_chache
`Article.reset_counters(article.id, :comments)`
On basic Rails i mplementation one must remeber that cunter cashe is updated on callbacks, and so when running commands that do not trigger them one can **desynchronize** values. Which then should be senc again with previous method