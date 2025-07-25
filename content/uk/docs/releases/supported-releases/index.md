---
title: Підтримувані релізи
description: Поточні підтримувані релізи Istio.
weight: 36
aliases:
    - /uk/about/supported-releases
    - /latest/uk/about/supported-releases
owner: istio/wg-docs-maintainers
test: n/a
---

Ця сторінка містить інформацію про статус, графік та політику підтримки для поточних релізів. Підтримувані релізи Istio включають релізи, що знаходяться в активному періоді підтримки та отримують патчі для виправлення безпеки та помилок. Наступні патч-релізи на мажорному релізі не містять несумісних змін.

- [Політика підтримки](#support-policy)
- [Схема іменування](#naming-scheme)
- [Різниця між панелями управління та даних](#control-planedata-plane-skew)
- [Статус підтримки релізів Istio](#support-status-of-istio-releases)
- [Підтримувані релізи без відомих загальних вразливостей (CVE)](#supported-releases-without-known-common-vulnerabilities-and-exposures-cves)
- [Підтримувані версії Envoy](#supported-envoy-versions)

## Політика підтримки {#support-policy}

Ми створюємо нові збірки Istio для кожного коміту. Орієнтовно раз на квартал ми створюємо мажорний реліз і проводимо кілька додаткових тестів, а також кваліфікацію релізу. Ми випускаємо патч-версії для проблем, виявлених у мажорних релізах.

Різні типи релізів представляють різний рівень якості продукту та рівень підтримки від спільноти Istio. У цьому контексті *підтримка* означає, що спільнота буде випускати патч-релізи для критичних проблем і надавати технічну допомогу. Окремо, треті сторони та партнери можуть пропонувати довгострокові рішення підтримки.

| Тип               | Рівень підтримки                                                                                                                         | Якість і рекомендоване використання                                                                              |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| Збірка для розробників | Немає підтримки                                                                                                                            | Небезпечно, може бути ненадійним. Корисно для експериментів.                                                       |
| Мажорний реліз    | Підтримка надається до 6 тижнів після релізу N+2 (наприклад, 1.11 підтримується до 6 тижнів після релізу 1.13.0)                             |
| Патч              | Те ж саме, що й відповідний Мажорний реліз                                                                                              | Користувачам рекомендується застосовувати патч-релізи, як тільки вони стають доступними для даного релізу.            |
| Патч безпеки      | Те ж саме, що й Патч, але містить виправлення безпеки. Іноді патчі безпеки можуть містити додатковий код/виправлення окрім виправлень безпеки. | З огляду на природу виправлень безпеки, користувачам **рекомендовано** застосовувати патчі безпеки після випуску.      |

Ви можете знайти доступні релізи на [сторінці релізів](https://github.com/istio/istio/releases), а якщо ви любите пригоди, ви можете дізнатися про наші розробницькі збірки на [вікі розробницьких збірок](https://github.com/istio/istio/wiki/Dev%20Builds). Високорівневі нотатки релізів для кожного мажорного та патч-релізу можна знайти [тут](/news).

## Схема іменування {#naming-scheme}

Наша схема іменування є такою:

{{< text plain >}}
<major>.<minor>.<patch>
{{< /text >}}

де `<minor>` збільшується з кожним релізом, а `<patch>` відзначає кількість патчів для поточного `<minor>` релізу. Патч зазвичай є невеликим змінами в порівнянні з `<minor>` релізом.

## Різниця між панелями управління та даних {#control-planedata-plane-skew}

Панель управління Istio може бути однією версією попереду панелі даних. Проте, панель даних не може бути попереду панелі управління. Ми рекомендуємо використовувати відповідні [версії](#control-planedata-plane-skew), щоб уникнути будь-якої різниці.

На даний момент, панель даних до панелі даних сумісна з усіма версіями; однак це може змінитися в майбутньому.

## Статус підтримки релізів Istio {#support-status-of-istio-releases}

{{< support_status_table >}}

## Підтримувані релізи без відомих загальних вразливостей (CVE) {#supported-releases-without-known-common-vulnerabilities-and-exposures-cves}

{{< warning >}}
Istio не гарантує, що мінорні релізи, які виходять за межі вікна підтримки, мають всі відомі CVE виправленими. Будь ласка, дотримуйтеся останніх версій та використовуйте підтримувану версію.
{{< /warning >}}

| Мінорні релізи | Виправлені версії без відомих CVE |
|----------------|-----------------------------------|
| 1.26.x         | 1.26.0+                           |
| 1.25.x         | 1.25.3+                           |
| 1.24.x         | 1.24.6+                           |

## Підтримувані версії Envoy {#supported-envoy-versions}

Data plane Istio базується на [Envoy](https://github.com/envoyproxy/envoy).

Звʼязок між версіями двох проєктів:

| Версія Istio | Гілка релізу Envoy |
|--------------|--------------------|
| 1.26.x        | release/v1.34     |
| 1.25.x        | release/v1.33     |
| 1.24.x        | release/v1.32     |

Ви можете знайти точний коміт Envoy, який використовується Istio [в репозиторії `istio/proxy`](https://github.com/istio/proxy/blob/{{< source_branch_name >}}/WORKSPACE#L26): шукайте змінну `ENVOY_SHA`.
