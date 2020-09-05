# Ruby Benchmarking — Iterations per Second

{% embed url="https://github.com/evanphx/benchmark-ips" %}

`benchmark-ips` adds iterations per second features to Ruby's Benchmark. This means that `benchmark-ips` will run a given snippet of code repeatedly for 5 seconds \(default\) and count how many times it was able to execute.

### Example

`Array#map` vs `Array#each`

```ruby
require 'benchmark/ips'

numbers = [1, 2, 3, 4, 5]

Benchmark.ips do |benchmark|
  benchmark.config(time: 5, warmup: 2)

  benchmark.report("map") do
    numbers.map { |number| number + 1 }
  end

  benchmark.report("each") do
    new_numbers = []
    numbers.each do |number|
      new_numbers << number + 1
    end
  end

  benchmark.compare!
end
```

#### Results

```text
Warming up --------------------------------------
                 map   307.475k i/100ms
                each   269.392k i/100ms
Calculating -------------------------------------
                 map      3.127M (± 0.7%) i/s -     15.681M in   5.014498s
                each      2.745M (± 1.3%) i/s -     13.739M in   5.006861s

Comparison:
                 map:  3127347.5 i/s
                each:  2744536.5 i/s - 1.14x  (± 0.00) slower
```

Learned from [Aaron Pattersons' Variety Show \(RailsConf 2020.2 Talk\)](https://railsconf.com/2020/video/aaron-patterson-aaron-patterson-s-variety-show)

