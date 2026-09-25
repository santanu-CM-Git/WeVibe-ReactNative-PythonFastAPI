# WeVibe

**Every conversation has a story.**

WeVibe is an AI-powered conversation analysis app for iOS and Android. Record a talk or paste a transcript, and WeVibe turns it into clear insights on personality, emotion, and group dynamics — so people can communicate with more awareness and confidence.

> **Website**: [wevibeapp.app](https://wevibeapp.app) · **API**: [api.wevibeapp.app](https://api.wevibeapp.app)

# Overview

- **Platform**: React Native (iOS & Android)
- **Category**: Communication intelligence / personal insight
- **Model**: Freemium → WeVibe Pro
- **Backend**: Python FastAPI
- **Database**: MySQL

# The Problem

Conversations move fast. In meetings, coaching sessions, dates, and team discussions, people often walk away unsure of what was really said — or how they came across.

Traditional notes and recordings capture *what* happened. They rarely explain:

- How each person showed up (tone, style, personality signals)
- What emotions ran under the surface
- How the group dynamic shaped the outcome

That gap leaves professionals, couples, coaches, and teams guessing instead of improving.

# The Solution

WeVibe closes that gap with a simple loop:

1. **Choose a context** — Work, Team, Coaching, Relationship, Dating, or Social
2. **Capture the conversation** — Record live audio (up to ~60 minutes) or paste a transcript
3. **Get a structured report** — Overview score, speaker psychology, emotions, and group dynamics
4. **Act on it** — Reflect, share a PDF, or revisit past analyses from history

Insights are framed as **awareness tools, not clinical diagnosis** — with explicit consent and privacy messaging built into onboarding.

# Who It’s For

- **Professionals & teams** — Clearer meeting dynamics and communication patterns
- **Coaches & facilitators** — Structured feedback after sessions
- **Couples & partners** — Emotional awareness without judgment
- **People in dating / social settings** — Confidence through better self-understanding

# Core Experience

## Onboarding

Splash → How it works → Consent (participant permission required) → Sign up / Log in → Home.

Returning users land on the dashboard after auth hydrate — no repeated splash stack.

## New analysis

Home → **New analysis** → Topic → Record (audio or transcript) → Processing → Report.

If free quota is used up, the flow routes to the WeVibe Pro paywall first.

## Report

Three lenses on the same conversation:

- **Overview** — Conversation-level score and summary
- **Speakers** — Personality frameworks (e.g. Big Five, DISC, MBTI-like, Enneagram), emotional signals, communication style
- **Group** — Dynamics across participants

Users can export and share a PDF from the report.

## Account & Pro

Plan status, restore purchases, password management, and legal links (About, Privacy, Terms, Delete account) via the marketing site.

# Product Positioning

- **Speaker insights** — Understand how each person shows up
- **Emotional awareness** — Surface tone and feeling under the words
- **Privacy first** — Consent-led use; insights, not diagnosis

**Tagline direction from product copy:**

- *Understand the vibe of every conversation.*
- *WeVibe reveals key insights from your talks to strengthen relationships and boost confidence.*

# Business Model

- **Free** — First **2** analyses
- **WeVibe Pro** — Unlimited analyses and deeper Pro features

Subscriptions are handled with **RevenueCat** (Apple / Google entitlement: `WeVibe Pro`), synced with the WeVibe backend so quota and Pro status stay server-authoritative.

Approximate list pricing (client fallbacks): monthly ~$9.99 · annual ~$79.99.

# Tech Stack

## Mobile app

- React Native 0.86, React 19, TypeScript
- Redux Toolkit + RTK Query, JWT auth, AsyncStorage
- `react-native-nitro-sound` for recording (local M4A → multipart upload)
- RevenueCat (`react-native-purchases`) for subscriptions
- HTML → PDF + native share for report export
- Soft lavender brand system — Instrument Serif + Plus Jakarta Sans, purple CTAs

## Backend

- **API**: Python **FastAPI** (REST)
- **Database**: **MySQL**
- Base URL: `https://api.wevibeapp.app`
- Key routes: `/auth`, `/analyze/audio`, `/analyze/transcript`, `/analyze/history`, `/subscription/*`

## Architecture notes

- Analysis is **async request/response** (not live WebSocket chat)
- Audio jobs use a longer client timeout (~120s) to match server processing
- Free-limit enforcement can come from the API (`403 FREE_LIMIT_REACHED`) as well as local fallbacks
- Raw analysis payloads are mapped into UI view-models for Overview / Speakers / Group

# Design Language

Calm, premium wellness-meets-productivity aesthetic:

- Soft lavender wash backgrounds and gentle top gradients
- Primary purple CTAs (`#7C6DFA` family)
- Topic chips in soft pastels by context
- Rounded, airy layouts with brain / insight imagery — not dense “dashboard” chrome

# Outcomes

1. **Faster clarity** after hard or high-stakes conversations
2. **Better self-awareness** of tone and style
3. **Stronger relationships** at work and at home through shared language
4. **Habitual reflection** via saved history and exportable reports

# Getting Started

> **Note**: Make sure you have completed the [Set Up Your Environment](https://reactnative.dev/docs/set-up-your-environment) guide before proceeding.

## Step 1: Start Metro

```sh
# Using npm
npm start

# OR using Yarn
yarn start
```

## Step 2: Build and run your app

### Android

```sh
# Using npm
npm run android

# OR using Yarn
yarn android
```

### iOS

Install CocoaPods dependencies (first clone or after updating native deps):

```sh
bundle install
bundle exec pod install
```

Then run:

```sh
# Using npm
npm run ios

# OR using Yarn
yarn ios
```

## Step 3: Modify your app

Open `App.tsx` in your text editor. Changes are reflected via [Fast Refresh](https://reactnative.dev/docs/fast-refresh).

- **Android**: Press the <kbd>R</kbd> key twice or open the **Dev Menu** via <kbd>Ctrl</kbd> + <kbd>M</kbd> (Windows/Linux) or <kbd>Cmd ⌘</kbd> + <kbd>M</kbd> (macOS).
- **iOS**: Press <kbd>R</kbd> in iOS Simulator.

# Summary

WeVibe takes something ephemeral — a conversation — and turns it into a private, structured insight product. By combining recording or transcripts, context-aware analysis, and a clear freemium path to Pro, it serves anyone who wants to **understand the vibe**, not just replay the words.

# Learn More

- [WeVibe website](https://wevibeapp.app)
- [Privacy](https://wevibeapp.app/privacy)
- [Terms](https://wevibeapp.app/terms)
- [About](https://wevibeapp.app/about)
- [React Native docs](https://reactnative.dev/docs/getting-started)
