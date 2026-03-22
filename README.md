# Distributed Web Crawling and Search System

This repository contains a distributed systems course project that crawls web pages, indexes their contents, and supports basic search over the collected data.

The system is organized into several cooperating node types:

- `master.py` starts a crawl, accepts seed URLs and crawl depth, distributes work, and serves the final search CLI.
- `master_backup.py` acts as a standby coordinator and takes over if the primary master stops sending heartbeats.
- `crawler.py` receives crawl tasks, renders pages, extracts links and text, stores page data, and forwards content for indexing.
- `indexer.py` consumes crawled content, builds a Whoosh index, and answers search queries after indexing completes.

Communication between nodes is handled through AWS SQS FIFO queues, with S3 used for storing crawled content and the generated index archive.

For setup and execution steps, see `README.txt`. For the full design and implementation details, see the report in the repository: `Distributed_Report.pdf`. The original project specification PDFs, `req_spec_simple.pdf` and `req_spec.pdf`, are also included.
