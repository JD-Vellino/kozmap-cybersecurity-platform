# KozMap — Cybersecurity Platform

**Deterministic security state. Evidence-bound AI investigation. A live model of the environment.**

> **Public showcase.** KozMap is a privately developed cybersecurity platform. This repository presents the product, its architecture and its operating principles without exposing production source code or sensitive implementation details.

<p align="center">
  <img src="assets/kozmap-main-map.png" alt="KozMap live cybersecurity map" width="100%">
</p>

<p align="center">
  <strong><a href="assets/kozmap-main-page.webm">▶ Watch the live map demo</a></strong>
</p>

## What is KozMap?

KozMap is a cybersecurity platform designed to turn fragmented telemetry into a persistent, explainable model of an environment.

Instead of treating the SOC as a stream of disconnected alerts, KozMap brings assets, virtual machines, sensor coverage, network activity, evidence, hypotheses, attack chains and incidents into one stateful system.

The main workspace is a spatial security map: physical systems form the environment, virtual machines remain visually attached to their hosts, sensors show where visibility exists, and network activity moves between the systems involved.

The purpose is not visual novelty. It is to reduce the amount of mental reconstruction required before an analyst can understand what is happening.

## Core design

| Principle | KozMap approach |
| --- | --- |
| **Deterministic security state** | Evidence, lifecycle and security state exist independently of the AI layer. |
| **Evidence before inference** | Observations, deterministic context and model interpretation remain distinguishable. |
| **Source-agnostic telemetry** | Multiple network, endpoint and runtime sources can contribute evidence without any one source becoming “the truth.” |
| **Evidence-bound AI** | AI investigates retrieved evidence and structured context rather than inventing the underlying state. |
| **Truthful uncertainty** | Missing visibility remains visible; unknown is not silently converted into safe. |
| **Human-readable operations** | Map, timeline, chains, incidents and investigation views are different views of the same security model. |

## High-level architecture

<p align="center">
  <img src="assets/kozmap-architecture.svg" alt="KozMap public architecture overview" width="100%">
</p>

### Observation

KozMap accepts telemetry from multiple network, endpoint and runtime sources. Native observations retain their provenance while the platform builds a consistent security view.

The architecture is deliberately not tied to one SIEM or one sensor vendor.

### Deterministic evidence & state

The authoritative layer is deterministic.

Observed events can contribute to evidence, hypotheses, chains and incidents. Coverage state, lifecycle transitions, causality and audit history are maintained separately from model reasoning.

That boundary allows the system to remain reproducible and inspectable even as AI models evolve.

### Investigation

AI sits above the deterministic floor.

KozMap uses bounded local analysis for first-pass triage and **Astra** for deeper investigation. The reasoning layer works from structured context and retrieved evidence; it does not own or rewrite the underlying security truth.

> **AI interprets evidence. It does not manufacture security truth.**

## A spatial model of the environment

KozMap uses a consistent visual language to make infrastructure and security state understandable at a glance.

Physical endpoints act as primary systems. Virtual machines remain associated with their host. Sensor presence and evidence state surround the assets they observe. The gateway represents the network edge, and observed traffic moves across factual source-to-destination relationships.

The interface distinguishes concepts that traditional dashboards often collapse together: current activity versus remembered topology, event freshness versus sensor health, sensor health versus asset coverage, observation versus ownership, hypothesis versus confirmed incident.

## Product surfaces

The private platform currently includes the **Map**, **Overview**, **AI Room**, **Incidents**, **Timeline**, **Chains**, **Hypotheses**, **Suppressions**, **Audit Log**, **Search**, administration and reporting surfaces.

These are not separate data silos. They are different operational views over the same evidence and state model.

## Evidence-bound reasoning

Astra is designed around explicit epistemic constraints that matter in real investigations.

KozMap keeps distinctions such as event freshness, runtime health and asset coverage separate. An observed network peer is not automatically declared an owned asset. Advisory ATT&CK metadata is not treated as proof. Incomplete evidence is not presented as exhaustive. Unsupported conclusions remain unresolved.

The goal is useful AI reasoning without allowing model confidence to overwrite evidentiary reality.

## Public / private boundary

The production platform is private by design.

This repository intentionally contains only the public product layer: selected visuals, high-level architecture, product concepts and engineering principles. It does **not** publish production source code, private APIs, deployment configuration, credentials, detection logic, database internals, model prompts, investigation broker internals or customer data.

## Status

KozMap is under active private development.

This repository exists to show what the platform is, the problems it is designed to solve, and the engineering philosophy behind it — without turning the production system into an open-source release.

---

**KozMap** · Cybersecurity platform for deterministic state, evidence-driven investigation and spatial security operations.
