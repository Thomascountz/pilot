# Ruby Benchmarking — Iterations per Second

{% embed url="https://github.com/evanphx/benchmark-ips" %}

`benchmark-ips` adds iterations per second features to Ruby's Benchmark. This means that `benchmark-ips` will run a given snippet of code repeatedly for 5 seconds \(default\) and count how many times it was able to execute.

### Example

Keyword args vs. option hash vs. frozen constant option hash vs. splat on receiver vs. splat on receiver and caller

```ruby
require 'benchmark/ips'

Benchmark.ips do |benchmark|
  benchmark.config(time: 5, warmup: 2)


  benchmark.report("keyword-args") do
    def foo(a: nil, b: nil, c: nil, d: nil, e: nil)
      bar(a: a, b: b, c: c, d: d, e: e)
    end

    def bar(a: nil, b: nil, c: nil, d: nil, e: nil)
      e
    end

    foo()
  end

  benchmark.report("opts-hash") do
    def foo(args={})
      bar(args)
    end

    def bar(args={})
      args[:e]
    end

    foo()
  end

  ARGS = {}.freeze
  benchmark.report("opts-hash-constant") do
    def foo(args=ARGS)
      bar(args)
    end

    def bar(args=ARGS)
      args[:e]
    end

    foo()
  end

  benchmark.report("opts-splat") do
    def foo(**args)
      bar(args)
    end

    def bar(args)
      args[:e]
    end

    foo()
  end

  benchmark.report("caller-splat") do
    def foo(**args)
      bar(**args)
    end

    def bar(**args)
     args[:e]
    end

    foo(**{})
  end

  benchmark.compare!
end

```

#### Results

```text

Warming up --------------------------------------
        keyword-args   115.618k i/100ms
           opts-hash   113.442k i/100ms
  opts-hash-constant   116.818k i/100ms
          opts-splat   111.250k i/100ms
        caller-splat    94.542k i/100ms
Calculating -------------------------------------
        keyword-args      1.156M (± 1.2%) i/s -      5.781M in   5.002661s
           opts-hash      1.123M (± 1.3%) i/s -      5.672M in   5.050629s
  opts-hash-constant      1.162M (± 0.9%) i/s -      5.841M in   5.028786s
          opts-splat      1.110M (± 0.9%) i/s -      5.562M in   5.011539s
        caller-splat    948.735k (± 1.1%) i/s -      4.822M in   5.082830s

Comparison:
  opts-hash-constant:  1161595.6 i/s
        keyword-args:  1155730.1 i/s - same-ish: difference falls within error
           opts-hash:  1123228.9 i/s - 1.03x  (± 0.00) slower
          opts-splat:  1110022.7 i/s - 1.05x  (± 0.00) slower
        caller-splat:   948734.7 i/s - 1.22x  (± 0.00) slower
```

Learned from [Aaron Pattersons' Variety Show \(RailsConf 2020.2 Talk\)](https://railsconf.com/2020/video/aaron-patterson-aaron-patterson-s-variety-show)

