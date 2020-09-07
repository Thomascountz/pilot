# Ruby Profiling & Benchmarking

## Benchmarks, Profiles, & Metrics

**Benchmark**: "...a synthetic measurement of resources or time consumed by a defined procedure." —[Nate Berkopec](https://www.youtube.com/watch?v=XL51vf-XBTs)

Benchmarks are usually taken in production-like environments, which is why we call it a "synthetic" measurement. Not only can yo benchmark time \(e.g.`iter/s` or `ms`\) we can measure the amount of resources used \(e.g. no. of objects allocated, MB of memory used\). These measurements are usually taken by running a single proedure \(e.g. line of code, method\) multiple times and then collecting an aggregated result.

**Profile**: "...a step-by-step accounting of the relative consumption of resources by a procedure's many subroutines." —[Nate Berkopec](https://www.youtube.com/watch?v=XL51vf-XBTs)

Rather than getting a single result at the end, like benchmarking, a profile tells us _what/where_ we've spent our time, sometimes down to the method or even line number. The results are relative in that is shows how much time we've spent in a given subroutine relative to the entire operation. \(e.g. 10% of time was spent in this method, relative to the entrypoint of the profiler\). Like benchmarks, profiles can also measure time or resources.

**Production Metrics**: performance metrics logged while real users interact with the application in production.

After deploying your application to production, it's a good idea to collect high-level measurements that reflect what your user experiences. These often show up in a type of logging tool, and can include measurements like page-load time, memory usage, cache misses.

## Process

* Read Production Metrics
* Profile to Find Bottlenecks
* Take Benchmark Measurements
* \(Iterate & Deploy\)

### Read Production Metrics

The performance optimization journey begins with the user. What is their experience like and can we quantify what it means to be "suboptimal?" It's said that if you're not starting here, you may be prematurely optimizing.

#### Premature optimization

Increasing performance often isn't free; it's about tradeoffs. If we place performance above-all-else, we'll need to make sacrifices in other areas, \(just like premature abstractions\). In order to make sure our tradeoffs are worth it, we want to start by quantifying the problem and tying it back to our users in production.

### Profile to Find Bottlenecks

#### Profiling Environment

In order to profile out application, we want as close to a production environment as possible. In a Rails application, these often means ensuring that we have production-like data in terms of shape and scale. In some instances, this is easy \(take a production dump of the database\), but when we aren't able to use production data locally \(because of scale or privacy, for example\), then crafting seed data may be our only recourse.

#### Production-like Code Execution

By default, Rails runs differently in production than it does in development. 

#### CPU v. Wall Time

CPU time counts time based on CPU cycles \(waiting on I/O and `sleep`-ing isn't counted\). Wall time is the time "on the clock on the wall\) or stopwatch time.

#### Statistical v. Tracing

Statistical profilers sample a percentage of the stackframe by interrupting the process, capturing a snapshop, and then aggregating a result. A tracing profiler hooks into the language runtime and records the stack in real time, meaning you'll have a more accurate result.

#### StackProf & Ruby-Prof

StackProf is statistical. Ruby-Prof is tracing. 

#### memory\_profiler

#### rack-mini-profiler

### Take Benchmark Measurements

#### Micro, Macro, & App

Micro benchmarks measure very small scopes: a few dozen lines of code. A macro benchmark zooms out a little and may be something like benchmarking a service object. An app benchmark is the widest scope and is what you might right to benchmark a controller action.

Micro benchmarks should be written with the number of times those lines of code are run in mind. For example, if you take a benchmark of a single method, but that method is only called once per request, even a large change in performance there might not gain us a lot.

An app benchmark might make it difficult to see improvements. Making changes to the code might not result in a noticeable change in the benchmark.

#### benchmark\_ips

`benchmark_ipsa` adds object allocation measurements.

Warmup is used to allow code execution to reach a steady state. A second run of code is always faster than the first, up until the point of steady state.

Benchmark time should be long enough for low variance. If the standard variation is high \(&gt; 5%\), try increasing the benchmark time.

> Check in benchmarks to a /benchmark folder in the repo



