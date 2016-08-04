+++
date = "2016-08-02T17:25:07-04:00"
draft = false
title = "Active Record Queries"

+++

Substitue "Model" with your model:

```ruby
Model.first
# find the first record

Model.last
# find the last record

Model.find_by(attribute: 'value')
# find the record by a specific attribute

Model.order(:attribute)
# order the records by the attribute - ascending is default

Model.order(:attribute :desc)
# order the records by the attribute, use descending order

Model.where(attribute: 'value')
# returns all records where the attribute equals the given value

Model.where('attribute > ?', 'value')
# returns all records where the attribute is greater than the given value

Model.where('attribute LIKE ?', '%value%')
# returns all records where the attribute is similar to the value. The % sign on each side means anything can be before or after - very general search

Model.where('attribute LIKE ? AND other = ?', '%value%', 'other_value')
# returns all records where the attribute is similar to the value AND other is equal to the other value

Model.where('attribute LIKE? OR other = ?', '%value%', 'other_value')
# returns all records where the attribute is similar to the value OR other is equal the other value
```
