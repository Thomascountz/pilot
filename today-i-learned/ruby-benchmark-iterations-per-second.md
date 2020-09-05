# Ruby Benchmark — Iterations per Second

{% embed url="https://github.com/evanphx/benchmark-ips" %}

`benchmark-ips` adds iterations per second features to Ruby's Benchmark. This means that `benchmark-ips` will run a given snippet of code repeatedly for 5 seconds \(default\) and count how many times it was able to execute.

### Example

This example is from [Aaron Pattersons' Variety Show \(RailsConf 2020.2 Talk\)](https://railsconf.com/2020/video/aaron-patterson-aaron-patterson-s-variety-show)

```ruby
require 'benchmark/ips'

Benmarck.ips do |x|
  x.report("where with ids") do
    Post.where(id: ids)
  end
  
  x.report("where with sanitize") do
    Post.where(ActiveRecord::Base.sanitize_sql(["id IN ?"), ids])
  end
  
  x.compare!
end
```

#### Results

```text
Warming up -------------------------------------
       where with ids     81.000    i/100ms
  where with sanitize    146.000    i/100ms
Calculating ------------------------------------
       where with ids     793.197  (± 3.9%) i/s -     3.969k in 5.011711s
  where with sanatize       1.377k (± 8.5%) i/s -     6.862k in 5.030918s


Comparison:
       where with ids     1376.6 i/s
  where with sanitize      793.2 i/s - 1.74x slower
```

