Concerns
Rails includes [Active Support’s Concerns](https://goodscary.us1.list-manage.com/track/click?u=8978f575757c4b55d2a353a62&id=01476e0722&e=d9063823d8) as a way to group functionality that’s used in multiple places. It’s a wrapper around a standard Ruby `module`.

### `app/models/concerns/orderable_by_timestamp.rb`

```
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

```
class Book < ApplicationRecord
  include OrderableByTimestamp
end
```

This module could also be included in other models and provide the same functionality

Concers should be small so that when included into models do not overburden them with unnecessery methods
Use with coution