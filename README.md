# LOGO5 by SoulFlame

LOGO5 е AI платформа за логопедична работа с три продуктови режима: **Логопед**, **Родител** и **Център/училище**.

Production: https://logo5.vercel.app

## Какво работи сега

- публична landing страница с ясни режими
- заявка за консултация
- календар и локален UX за часове
- локална карта на детето за демо/прототип
- безопасен LOGO5 AI помощник с червени флагове и структурирани следващи стъпки
- база знания от Supabase
- терапевтичен workspace за оценка → план → упражнения → документи → напредък
- клинична Supabase схема с RLS
- отделни роли: parent / therapist / admin
- защита срещу self-promotion на роля
- родители могат да четат своите клинични записи; клиничното авторство е ограничено до назначения логопед
- consent metadata за публичните заявки
- Vercel production deployment от `main`

## Важно разграничение

4-цифреният код в текущия frontend е **само локално удобство на конкретното устройство**. Той не отключва сървърни здравни данни и не се представя като защитена медицинска идентичност.

Реалните клинични досиета трябва да се отварят само след Supabase Auth и RLS-проверка.

## Данни и сигурност

Клиничните таблици използват префикс `logo5_`:

- `logo5_profiles`
- `logo5_children`
- `logo5_assessments`
- `logo5_plans`
- `logo5_sessions`
- `logo5_messages`
- `logo5_documents`
- `logo5_knowledge`
- `logo5_appointment_requests`

Публичният visitor има само минимален достъп: публикувани knowledge записи и INSERT на consented appointment request.

## AI правило

LOGO5 AI:
- не поставя диагнози
- разделя наблюденията от възможните обяснения
- показва липсваща информация
- предлага какво да се провери
- дава безопасни следващи стъпки
- прекратява обикновените препоръки при медицински червен флаг

Клиничните решения остават при квалифициран специалист.

## Следващ production етап

1. Supabase Auth за родител/логопед
2. реален cross-device parent portal
3. therapist dashboard с CRUD към клиничните таблици
4. генератор на Word/PDF документи
5. измерими цели и session progress
6. storage за документи/аудио със signed URLs
7. DAVID orchestration / RAG слой зад защитен endpoint
8. audit log, export/delete workflow и GDPR retention правила
9. center/organization tenancy
10. speech-analysis модул като отделна предварителна AI оценка

## Stack

- Frontend: static HTML/CSS/JS
- Hosting: Vercel
- Database/Auth: Supabase
- AI orchestration target: DAVID
