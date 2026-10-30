# OSINT / детектив / юрист — сборник промптов и скиллов

Собрано 24.10.2026. Только бесплатные и открытые материалы.

## prompts/
- `01-detective-lawyer-osint-master.md` — ваш мастер-промпт «детектив-юрист-OSINT»: оригинал и **вариант для РФ** (рекомендуется).
- `02-prompts-chat-source-hunting-osint-mode.md` — «Source-Hunting / OSINT Mode» с prompts.chat (CC0). Заточен под слежку в США; для РФ берите как образец структуры.
- `03-dev-to-5-phase-prompts.md` — 5 промптов по фазам Scope → Collect → Pivot → Verify → Document (DEV Community).

## skills/
- `yuridicheskiy-analiz-rf/SKILL.md` — скилл юридической оценки OSINT-техник (🟢/🟡/🔴) по праву РФ. Основной.
- `analise-juridica/SKILL.md` — исходник того же скилла (право Бразилии, португальский), с SkillsMP. Для справки.

## osint-investigator/ (GitHub: TNeagle/osint-investigator)
Полный агент на английском (местами встречаются фразы на китайском):
- `OSINT_Agent_System_Prompt.md` — системный промпт координатора с под-ролями.
- `SKILL.md`, `skill-report-template.md`, `skill-insight-engine.md`, `skill-networkx-schema.md`.
- `references/` — 22 плейбука: `playbook-legal.md` (суды и решения), `playbook-person.md`, `playbook-enterprise.md`, `playbook-financial.md`, `playbook-crypto.md`, `playbook-real-estate.md`, `playbook-scam.md`, `playbook-social-media.md`, `playbook-geolocation.md` и др., плюс `osint-sources-guide.md`.
- `scripts/` — скрипты анализа связей (Python, нужны библиотеки networkx и matplotlib) и pre/post-хуки. Хук `pre_investigate.sh` ищет JSON-графы в текущей папке и в домашней папке — запускайте в отдельной рабочей папке.
- Ориентирован на зарубежные источники; российские реестры подставляйте сами (см. вариант промпта для РФ).

## Как использовать
Используйте только для законных проверок: due diligence контрагента, свои активы, поручение клиента, журналистика. Перед любой нестандартной техникой прогоните её через `yuridicheskiy-analiz-rf`. Не является юридической консультацией.
