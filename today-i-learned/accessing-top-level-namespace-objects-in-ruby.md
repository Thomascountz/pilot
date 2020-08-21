# Accessing Top-Level Namespace Objects in Ruby

Ruby let's you use `::` not access objects at the top-level namespace, even when you're within a module that contains an object of the same name.

```ruby
# Top-level User
class User
  # -- snip --
end


module Moderator
  # Moderator::User
  class User
    def ban_user(user_id)
      ::User.find(user_id) # queries for the top-level User
      # -- snip --
    end
  end
end
```

In the above example, using `::` ensure that we're calling the `User` class in the top-level namespace. Without the double colon, `User.find` is equivilant to `Moderator::User.find`.

