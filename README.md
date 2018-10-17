### Rollout
---

.rb
https://github.com/fetlife/rollout

.io
https://github.com/rollout

```
gem install rollout

```

```ruby
require 'redis'
$redis = Redis.new
$rollout = Rollout.new($redis)

$rollout.set_feature_data(:chat, description: 'foo', release_data: 'bar', whatever: 'baz')
$rollout.active?(:chat, User.first)
$rollout.active?(:chat)

$rollout.activate_group(:chat, :all)
$rollout.define_group(:caretakers) do |user|
  user.caretaker?
end

$rollout.deactivate_group(:chat, :all)

$rollout.activate_user(:chat, @user)

$rollout.activate_percentage(:chat, 20)
CRC32(user.id) % 100_000 < percentage * 1_000
$rollout.deactivate_percentage(:chat)
$rollout = Rollout.new($redis, randomize_percentage: true)
$rollout.activate(:chat)
$rollout.activate?(:chat)
$rollout.deactivate(:chat)

$ns = Redis::Namespace.new(Rails.env, redis: $redis)
$rollout = Rollout.new($ns)
$rollout.activate_group(:chat, :all)


```

```

```
