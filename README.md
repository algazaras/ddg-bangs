# DuckDuckGo Bangs

Scraper and complete registry for [DuckDuckGo's bangs](https://duckduckgo.com/bang). The complete list of bangs can be found [here](https://duckduckgo.com/bang_lite.html).

- Scraper: [`bin/bangs`](bin/bangs);
- Registry:
  - JSON: [`data/bangs.json`](data/bangs.json);
  - YAML: [`data/bangs.yml`](data/bangs.yml).

To generate/update the registry, just run

```console
$ make
```

A full scraping is done the first time you run this, and results are cached in `data/bangs.db`, a SQLite database. Further runs are incremental.

Note that network problems (including temporary rate limiting from DDG's server side) could result in intermittent failures, in which case you will see "Error resolving !<bang>" messages. As long as the given bang is still valid (use `bin/bangs open <bang>` to test in your browser), just retry after a while; if a bang is being tried but in fact not valid, add it to `data/blacklist.txt`.

Run

```console
$ bin/bangs --help
```

for more details.

## Why

@jarun inadvertently presented me a challenge when he introduced to me his [ddgr](https://github.com/jarun/ddgr), to which he compared to [googler](https://github.com/jarun/googler):

> ... I am absolutely enjoying the DuckDyckGo Bang feature right from the terminal. ​Bangs allow you to native search ANY website, something we can never have with `googler` ...

Challenge accepted ;)

Some time later, out came this registry which could be plugged into any command line search tool.
