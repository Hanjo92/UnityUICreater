# Backlog

This backlog tracks likely next improvements for the repository after `v0.7.0`.

이 backlog는 `v0.7.0` 이후, 다음에 다듬을 만한 항목을 정리합니다.

## High Priority / 높은 우선순위

### 1. Runtime Verification

- extend the [recorded capability validation](docs/validation/2026-09-09-agent-capability-routing.md) to available Paseo/Claude/direct-API sessions and an actually vision-disabled runtime; record each session's own capabilities
- exercise authorized image generation through visual review, Unity import/assignment, and current-output screenshots when the required tools are available
- retain initial failures and corrected results, and distinguish fresh-session runs from follow-ups in an existing session

### 2. Example Expansion

- add more domain-shaped examples such as shop, reward screen, and profile screen
- add one example that compares two candidate repair strategies before choosing one

## Medium Priority / 중간 우선순위

### 3. Verification Set Expansion

- add one side-by-side verification example for tablet-capable layouts with explicit profile comparison

### 4. Platform Adapter Depth

- extend platform adapters with a few more service-specific usage examples
- tighten wording where a platform still sounds more generic than the Codex source skill

## Low Priority / 낮은 우선순위

### 5. Maintenance Automation

- consider a small automation or helper note for routine release prep
- consider a lightweight reminder pattern for syncing platform docs after larger skill releases
