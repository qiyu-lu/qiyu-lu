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

**[ragent-legacy](https://github.com/qiyu-lu/ragent-legacy)** — Agentic RAG service (Java 17,
Spring Boot 3.5, Milvus, React), rebuilt while studying [nageoffer/ragent](https://github.com/nageoffer/ragent):
multi-route retrieval, tree-structured intent classification, query rewriting, session memory,
MCP tool calls, and full-link tracing. Working through the trace layer end to end is what surfaced
the run-lifecycle bug I later fixed upstream.

**[ins-d-qpvt-tum](https://github.com/qiyu-lu/ins-d-qpvt-tum)** — lab tooling in Python: reads QPVT
frames from an Inertial Labs INS-D over serial and segments them into TUM ground-truth trajectories,
with a read-only viewer in a separate process so live plotting can never drop frames.

**[mini-spring](https://github.com/qiyu-lu/mini-spring)** — reimplementing Spring's IoC and AOP core
from scratch to understand the container rather than just configure it.

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
mapping, together with automation for running algorithms across benchmark datasets. The ROS 2 and
C++ contributions above came out of this work.

## Tech Stack

Backend & AI

<p>
  <img alt="Java" src="https://img.shields.io/badge/Java-007396?style=flat&logo=openjdk&logoColor=white">
  <img alt="Spring Boot" src="https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat&logo=springboot&logoColor=white">
  <img alt="MySQL" src="https://img.shields.io/badge/MySQL-4479A1?style=flat&logo=mysql&logoColor=white">
  <img alt="Redis" src="https://img.shields.io/badge/Redis-DC382D?style=flat&logo=redis&logoColor=white">
  <img alt="RocketMQ" src="https://img.shields.io/badge/RocketMQ-D77310?style=flat&logo=apacherocketmq&logoColor=white">
  <img alt="Elasticsearch" src="https://img.shields.io/badge/Elasticsearch-005571?style=flat&logo=elasticsearch&logoColor=white">
  <img alt="Milvus" src="https://img.shields.io/badge/Milvus-00A1EA?style=flat&logo=milvus&logoColor=white">
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
