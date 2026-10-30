# 5 OSINT-промптов по методу Scope → Collect → Pivot → Verify → Document
Источник: https://dev.to/sonotommy/osint-prompts-for-chatgpt-and-claude-5-templates-and-a-repeatable-method-4jnd (Tommaso Bertocchi, 9 июня 2026)

```
scope    -> what am I authorized to do, and what answer do I need?
collect  -> gather public data from real sources
pivot    -> turn one data point into the next (email -> username -> domain)
verify   -> challenge every finding, rate confidence, kill assumptions
document -> a report someone else could reproduce
```

## 1. Scoping
```
You are an OSINT analyst in the SCOPING phase. Do not collect or guess any
data yet.

Engagement: [one line on what you are authorized to investigate]
Objective: [the specific question you need answered]

Output:
1. A restated objective in one sentence.
2. In-scope vs out-of-scope (sources, identifiers, targets).
3. The 3-6 concrete questions that, if answered, satisfy the objective.
4. The public source types relevant to each question.
5. Legal/ethical flags I should confirm before proceeding.

Ask me anything ambiguous instead of assuming.
```

## 2. Email as a starting point
```
You are in the COLLECT and PIVOT phases. The seed is an email address:
[email]

List, as a checklist, the public-source checks worth running and what each one
could reveal:
- public breach/exposure datasets (presence only, no credential content)
- account discovery on public platforms tied to this address
- associated public profiles, avatars, and usernames
- domain of the email (if not a free provider) and what it implies

For each check, state: the data point it could produce, and the next pivot it
unlocks. Mark anything that requires live data I still need to fetch. Do not
fabricate results.
```

## 3. Username pivot across platforms
```
You are in the PIVOT and VERIFY phases. Seed username: [handle]

Produce a table of public platforms where this handle may exist. For each:
- platform
- how to confirm the account is the same person (signals: bio, links, avatar,
  writing style, cross-links)
- confidence: high / medium / low / unconfirmed
- what would raise or lower that confidence

Be explicit that handle reuse is not proof of the same person. Flag every
inference as an inference.
```

## 4. Domain and infrastructure
```
You are in the COLLECT phase. Target: [domain or IP]

Outline the public infrastructure checks and what each tells me:
- WHOIS / registration data and registrar
- DNS records (A, MX, NS, TXT) and what they reveal about hosting and email
- passive DNS and historically associated records
- related infrastructure (shared hosting, certificates, subdomains)
- hosting provider and ASN

For each, note the pivot it enables and whether I need to pull live data.
Output a structure I can drop findings into.
```

## 5. Verify and report
```
You are in the VERIFY and DOCUMENT phases. Here are my raw findings:
[paste findings]

Do three things:
1. For each finding, classify it as confirmed, probable, or assumption, and say
   what evidence supports it.
2. Attack the weakest links: what would make each finding wrong? What did I not
   check?
3. Produce a short report: objective, method, findings with confidence levels,
   gaps, and recommended next steps. Write it so another analyst could
   reproduce it.
```

Инструмент от автора: OpenOSINT (бесплатный, open source) — https://github.com/OpenOSINT/OpenOSINT
