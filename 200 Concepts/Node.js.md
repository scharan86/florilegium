---
tags:
  - cs/webdev/backend
created: 2026-03-24
status: draft
type: concept
aliases:
  - nodejs
---
---

>[!Definition]
>  Open-source and cross platform JS runtime environment. 

- Runs [[V8 JS]] engine, the core of Google Chrome. 
- Uses an [[Event Driven Architecture|event-driven]] and [[Non-blocking I/O|non-blocking I/O]] model.
- Its already running before you code even starts.
- Lightweight and efficient
- It runs in a single process without creating a new thread for every request. This allows it to serve far more concurrent requests with less memory. I.e, it serves all requests in a single thread using the event loop.
- Node.js provides a set of asynchronous I/O primitives in its standard library that prevent JavaScript code from blocking. 
- Node.js libraries are written using [[Non Blocking Paradigms|non-blocking paradigms]]
- New [[ECMAScript]] standards can be used without problems

>[!note]
>When Node.js performs an I/O operation, like reading from the network, accessing a database or the filesystem, instead of blocking the thread and wasting CPU cycles waiting, Node.js will resume the operations when the response comes back. This allows Node.js to handle thousands of concurrent connections with a single server without introducing the burden of managing thread concurrency, which could be a significant source of bugs.
>
>It moves to the next task and uses an event notification system to get the results when it's ready.

## Properties
1. [[Asynchronous]] and [[Event Driven Architecture|event-driven]]
2. [[Single-Threaded Architecture|Single threaded]] but highly scalable
3. No buffering
4. Blazingly fast

## Core Components


## Intuition





## Related Concepts
1. [[package.json]]