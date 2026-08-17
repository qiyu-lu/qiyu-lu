# qiyu-lu

**Java backend & AI application engineering · LiDAR-inertial odometry research**

I build backend services and AI applications in Java, and I do research on LiDAR-inertial odometry in
ROS/C++. The common thread is the same habit in both: take a system that already runs, find where it
breaks under real conditions, and prove the fix with evidence rather than a demo.

[Blog](https://qiyu-lu.github.io/) · Java 17 / Spring Boot · ROS 2 / C++

## Projects

**[local-deals-service](https://github.com/qiyu-lu/local-deals-service)** — high-concurrency coupon
flash-sale backend (Spring Boot). Reworked a tutorial-grade Redis Stream order pipeline into a
production-shaped one: RocketMQ transactional messages bind the Lua stock deduction to message
delivery, Canal replays the MySQL binlog into Elasticsearch (IK tokenizer + geo filtering in a single
query), WebSocket over Redis pub/sub pushes order results across instances, and a JMeter plus
fault-injection harness asserts MySQL / Redis / Stream / DLQ state instead of just the HTTP error rate.

**[ragent](https://github.com/qiyu-lu/ragent)** — industrial document RAG service for iron-ore domain
knowledge, built on [Ragent 1.1.0](https://github.com/nageoffer/ragent) (Java 17, Spring Boot 3.5,
PostgreSQL + pgvector). Reuses the upstream SSE, model-adapter and ingestion layers, and adds
structure-aware XLSX chunking with exact cell provenance, request-level retrieval, evidence-constrained
task closure, and a fixed regression evaluation set (3 documents, 24 questions, 15 parse anchors, with
hash-verified paired replay). Measured: oversized chunks 70 → 0 and duplicates 17 → 0; context precision
17.1% → 29.2% at half the average retrieved context, against Hit@5 95.2% → 90.5%. A fair-refill
mechanism that missed its quality gate stays behind a feature flag, default off. The project claims
better chunking, retrieval behaviour and auditability — not better answer accuracy, which held at 79.2%
strict pass either side of the change. Closing the trace-cancellation races here produced the upstream
PR below.

## Open Source

Merged upstream:

| Project | Contribution | PR |
| --- | --- | --- |
| [ccfos/huatuo](https://github.com/ccfos/huatuo) — eBPF Linux kernel observability (Go) | Unit tests for `SplitCommaList` and `ValueMatcher`; corrected a misleading retry-delay log in the Java profiler; `errcheck` cleanup | [#318](https://github.com/ccfos/huatuo/pull/318) [#321](https://github.com/ccfos/huatuo/pull/321) [#337](https://github.com/ccfos/huatuo/pull/337) [#338](https://github.com/ccfos/huatuo/pull/338) |
| [6-robot/jie_3d_nav](https://github.com/6-robot/jie_3d_nav) — ROS 2 3D navigation with a web UI | ROS 2 Foxy reproduction path, PCD map import, web map viewing fixes | [#1](https://github.com/6-robot/jie_3d_nav/pull/1) |
| [v4rl-ucy/ellipselio](https://github.com/v4rl-ucy/ellipselio) — ellipsoid-based LiDAR-inertial odometry | Experimental ROS 2 Foxy compatibility, merged as [`foxy-experimental`](https://github.com/v4rl-ucy/ellipselio/tree/foxy-experimental) | [#4](https://github.com/v4rl-ucy/ellipselio/pull/4) |
| [ouguangjun/kilo-map](https://github.com/ouguangjun/kilo-map) — LiDAR odometry and mapping | Fixed a crash from a missing `ImGui::End()` when the Selection panel is collapsed | [#2](https://github.com/ouguangjun/kilo-map/pull/2) |

Open for review: [nageoffer/ragent#80](https://github.com/nageoffer/ragent/pull/80) — finalize a trace
run as `CANCELLED` when the user aborts mid-stream · [scomup/likd-tree#1](https://github.com/scomup/likd-tree/pull/1)
— PCD nearest-neighbour search demo.

## Research

LiDAR-inertial odometry and mapping: degeneracy and uncertainty handling in the estimator,
continuous-time trajectory formulations, and fusing leg odometry on quadruped platforms. Most of it
lives in private research builds on top of FAST-LIO2, LIO-SAM, Traj-LO, LegKILO and voxel-based
mapping, together with automation for running algorithms across benchmark datasets and
[ins-d-qpvt-tum](https://github.com/qiyu-lu/ins-d-qpvt-tum) for turning INS-D serial output into TUM
ground-truth trajectories. The ROS 2 and C++ contributions above came out of this work.

## Tech Stack

Backend & AI

<p>
  <img alt="Java" src="https://img.shields.io/badge/Java-007396?style=flat&logo=openjdk&logoColor=white">
  <img alt="Spring Boot" src="https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat&logo=springboot&logoColor=white">
  <img alt="MySQL" src="https://img.shields.io/badge/MySQL-4479A1?style=flat&logo=mysql&logoColor=white">
  <img alt="Redis" src="https://img.shields.io/badge/Redis-DC382D?style=flat&logo=redis&logoColor=white">
  <img alt="RocketMQ" src="https://img.shields.io/badge/RocketMQ-D77310?style=flat&logo=apacherocketmq&logoColor=white">
  <img alt="Elasticsearch" src="https://img.shields.io/badge/Elasticsearch-005571?style=flat&logo=elasticsearch&logoColor=white">
  <img alt="PostgreSQL" src="https://img.shields.io/badge/PostgreSQL%20%2B%20pgvector-4169E1?style=flat&logo=postgresql&logoColor=white">
  <img alt="Docker" src="https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white">
</p>

Robotics & systems

<p>
  <img alt="C++" src="https://img.shields.io/badge/C++-00599C?style=flat&logo=cplusplus&logoColor=white">
  <img alt="ROS" src="https://img.shields.io/badge/ROS-22314E?style=flat&logo=ros&logoColor=white">
  <img alt="Python" src="https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white">
  <img alt="Linux" src="https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black">
  <img alt="Git" src="https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white">
</p>

## Writing

Algorithm reproduction notes and experiment records: [qiyu-lu.github.io](https://qiyu-lu.github.io/)
