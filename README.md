<h1 align="center">Hi, I'm qiyu 👋</h1>

<p align="center">
  <strong>Java backend & AI application engineering</strong><br>
  LiDAR-inertial odometry research
</p>

<p align="center">
  <a href="https://qiyu-lu.github.io/">Blog</a> ·
  <a href="https://github.com/qiyu-lu?tab=repositories">Projects</a>
</p>

---

## Focus

- **Backend & AI** — reliable workflows, RAG pipelines, search, and observability
- **Robotics** — LiDAR-inertial odometry, continuous-time estimation, and quadruped sensor fusion
- **Approach** — measurable improvements, reproducible tests, and explicit trade-offs

## Selected Projects

### [local-deals-service](https://github.com/qiyu-lu/local-deals-service)

A high-concurrency coupon backend evolved from a tutorial prototype into a reliability-focused system.
It combines RocketMQ transactional messaging, Canal-to-Elasticsearch sync, Redis-backed WebSocket
delivery, and fault-injection checks that verify business state—not only HTTP status.

`Java 8` · `Spring Boot` · `MySQL` · `Redis` · `RocketMQ` · `Elasticsearch`

### [ragent](https://github.com/qiyu-lu/ragent)

Built on [Ragent 1.1.0](https://github.com/nageoffer/ragent), this industrial-document RAG service adds
structure-aware XLSX chunking, exact cell provenance, leaner retrieval, and trace-cancellation handling.
On the fixed evaluation set, oversized chunks fell from `70 → 0` and duplicates from `17 → 0`; strict
answer pass remained `79.2%`.

`Java 17` · `Spring Boot` · `PostgreSQL` · `pgvector`

## Research & Open Source

I work on LiDAR-inertial odometry and mapping, with a focus on estimator degeneracy, continuous-time
trajectories, and leg-odometry fusion for quadruped platforms. I also maintain
[ins-d-qpvt-tum](https://github.com/qiyu-lu/ins-d-qpvt-tum), a small tool for converting INS-D serial
output into TUM ground-truth trajectories.

Merged contributions:

- [ccfos/huatuo](https://github.com/ccfos/huatuo) — tests, logging correction, and static-analysis cleanup ([PRs](https://github.com/ccfos/huatuo/pulls?q=is%3Apr+author%3Aqiyu-lu+is%3Amerged))
- [6-robot/jie_3d_nav](https://github.com/6-robot/jie_3d_nav) — ROS 2 Foxy reproduction and web map fixes ([#1](https://github.com/6-robot/jie_3d_nav/pull/1))
- [v4rl-ucy/ellipselio](https://github.com/v4rl-ucy/ellipselio) — experimental ROS 2 Foxy support ([#4](https://github.com/v4rl-ucy/ellipselio/pull/4))
- [ouguangjun/kilo-map](https://github.com/ouguangjun/kilo-map) — UI crash fix ([#2](https://github.com/ouguangjun/kilo-map/pull/2))

## Tools I Use

**Backend & AI:** `Java` · `Spring Boot` · `MySQL` · `Redis` · `RocketMQ` · `Elasticsearch` · `PostgreSQL / pgvector`

**Robotics & systems:** `C++` · `ROS 2` · `Python` · `Linux`
