---
title: "Static Site Generator performance considerations"
layout: learn
image:
  path: /images/learn/ssg-performance.png
  thumbnail: /images/learn/ssg-performance-400x225.png
---

When you start building large documentation sites, or gluing together multiple documentation sets, you might look for performance gains in the build time. Having smaller doc sites helps with this, so that you can build with your static site generator systems in parallel, but also look for incremental builds or ways to measure build times to look for areas where the build is slowed down and then find a root cause for the slower performance.

### Sphinx build performance options

Sphinx has a couple of possibilities for decreasing build times and increasing efficiency of builds.

Sphinx is configured by default to rebuild only new and changed files, rather than building the entire site over again. Use the `-a` flag on the `sphinx-build` command to always write all output files. This setting may help you measure benchmark values for build times.

Trying to keep your number of individual RST files to build to hundreds rather than thousands will naturally make the builds take less time. If you do need thousands of documents, then also be careful with the number of `toctree` directives in use as that overhead can slow down builds.

One option for large doc sets is to let Sphinx use multiple processes, adjusting on its own with the `sphinx-build -j auto` setting, available since the 1.7 release. The `auto` value causes Sphinx to use the number of CPUs for the number of parallel builds.

### Jekyll build time improvements

Jekyll can build only changed files with the incremental build feature, but it is considered experimental in the Jekyll 3.0 release. Use the `-I` or `--incremental` flag on your `jekyll build` or `jekyll serve` commands any time you want to re-build only posts and pages with changes.

```
$ jekyll build --incremental
```

For sites with about a hundred pages, there's less need for performance helpers, but when the site grows to 1,000 pages or more, you should consider only building changed files with the `--incremental` flag.

### Hugo build performance metrics

For Hugo, often the build is so fast you don't have to worry about building incremental changes. That said, Hugo does provide ways to benchmark the site build and to look for metrics for the templates themselves, because it is possible to slow down the build with inefficient template executions. When you run a `hugo` command, you can also use these flags to learn more about build performance:
    * `--stepAnalysis` - Display memory and timing of different steps of the program.
    * `--templateMetrics` - Display metrics about template executions.
    * `--templateMetricsHints` - Calculate some improvement hints when combined with --templateMetrics.

There's also the benchmark command, documented on the [gohugo.io site](https://gohugo.io/commands/hugo_benchmark/). The command builds the site multiple times with various flags set, and analyzes the running process to provide a benchmark for comparison either over time or with various flags set, such as including expired content.
