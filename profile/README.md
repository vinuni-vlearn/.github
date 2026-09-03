<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/vinuni-vlearn/.github/main/profile/assets/banner-dark.svg">
  <img alt="VLearn — the learning platform for the VinUni AI In Action programme" src="https://raw.githubusercontent.com/vinuni-vlearn/.github/main/profile/assets/banner-light.svg" width="100%">
</picture>

![Next.js 16](https://img.shields.io/badge/Next.js-16-134D8B?style=flat-square)
![React 19](https://img.shields.io/badge/React-19-134D8B?style=flat-square)
![FastAPI](https://img.shields.io/badge/FastAPI-Python%203.12-134D8B?style=flat-square)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-database-134D8B?style=flat-square)
![Pilot](https://img.shields.io/badge/stage-pilot-C72127?style=flat-square)
![4 repositories](https://img.shields.io/badge/repositories-4-5A5A5A?style=flat-square)

VLearn is VinUniversity's adaptive-learning web application, built for the
**AI In Action** programme. Learning is organised by published learning day: a
student opens today's day, works through its materials and assessment, and the
tutor adapts to what they have actually mastered.

<img src="https://raw.githubusercontent.com/vinuni-vlearn/.github/main/profile/assets/divider.svg" width="100%" alt="">

## What VLearn does

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/vinuni-vlearn/.github/main/profile/assets/features-dark.svg">
  <img alt="Learning days · Adaptive tutor · Markdown Lab Studio · Consent-aware telemetry" src="https://raw.githubusercontent.com/vinuni-vlearn/.github/main/profile/assets/features-light.svg" width="100%">
</picture>

Placement Assessment runs once per course and stays skippable. Every day carries
one post-class assessment plus targeted drills. Student identity always comes
from the server session — never from a role or email supplied by the interface.

<img src="https://raw.githubusercontent.com/vinuni-vlearn/.github/main/profile/assets/divider.svg" width="100%" alt="">

## How it fits together

```mermaid
flowchart LR
  B["Browser<br/>student · instructor"] --> FE["vlearn-frontend<br/>Next.js · BFF proxy"]
  FE -- "/api/backend/*" --> BE["vlearn-backend<br/>FastAPI"]
  BE --> DB[("PostgreSQL")]
  RP["Discord · web form"] --> BB["vlearn-bugbee"] --> BDB[("PostgreSQL")]

  classDef navy fill:#134D8B,stroke:#0E3C6E,color:#FFFFFF;
  classDef red fill:#C72127,stroke:#A31B20,color:#FFFFFF;
  classDef plain fill:#F2F6F9,stroke:#8C959F,color:#2E2E2E;
  class FE,BE,DB navy;
  class BB red;
  class B,RP,BDB plain;
```

The browser never talks to the API directly. Every authenticated call crosses the
same-origin BFF proxy in the frontend, which keeps the session cookie boundary
intact; Bedrock, S3 and SES sit behind hexagonal ports with mock adapters for
local development. Bug reports take their own path: they arrive through BugBee
and never touch the learning database.

Across all four repositories, `vlq` in **vlearn-quality** runs one quality gate
with the same commands each repository's CI runs — and counts a skipped check as
a failure.

<img src="https://raw.githubusercontent.com/vinuni-vlearn/.github/main/profile/assets/divider.svg" width="100%" alt="">

## Repositories

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/vinuni-vlearn/.github/main/profile/assets/repo-cards-dark.svg">
  <img alt="vlearn-frontend · vlearn-backend · vlearn-bugbee · vlearn-quality" src="https://raw.githubusercontent.com/vinuni-vlearn/.github/main/profile/assets/repo-cards-light.svg" width="100%">
</picture>

[vlearn-frontend](https://github.com/vinuni-vlearn/vlearn-frontend) ·
[vlearn-backend](https://github.com/vinuni-vlearn/vlearn-backend) ·
[vlearn-bugbee](https://github.com/vinuni-vlearn/vlearn-bugbee) ·
[vlearn-quality](https://github.com/vinuni-vlearn/vlearn-quality)

> [!NOTE]
> Every repository is private while VLearn is in pilot, so those links resolve
> only for members of this organisation.

---

<sub>VinUniversity · [vlearn.dev](https://vlearn.dev)</sub>
