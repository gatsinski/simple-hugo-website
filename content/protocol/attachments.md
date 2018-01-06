---
title: "Изпращане на писмо с прикачени файлове"
name: "attachments"
date: 2017-12-14T22:09:17+02:00
draft: false
order: 5
---

За изпращане на прикачени файлове в писмата се използва стандартът **MIME** (Multipurpose Internet Mail Extension). Той е предложен от лабораториите *Bell Communications* през 1991 г. Целта му е да се разширят възможностите на елетронната поща и да се позволи вмъкването в писмото на документи от различен тип (изображения, звук, текст и др.). Описан е в шест свързани документа, първият от които е <a href="https://tools.ietf.org/html/rfc2045">*RFC 2045*</a>.

MIME съдържа служебни символни описатели, които се използват за определяне на типа на прикачените към писмото документи, а също и за определяне на типа на документите, пренасяни чрез протокола HTTP.

Стандартът въвежда група заглавни данни (хедъри), които се добавят към всяко съобщение и предоставят информация, необходима за прочитането на съдържанието му.

- MIME-Version - За да се обозначи използването на MIME към съобщението се добавя хедър с версията. Обикновено тя е 1.0 и хедъра придобива вида "*MIME-Version: 1.0*".

- Content-Type - Този хедър индикира типа на мултимедииното съдържание на съобщението и се състои от тип и подтип.
  - Content-Type: text/plain
  - Content-Type: text/html
  - Content-Type: video/mpeg
  - Content-Type: image/jpeg
  - Content-Type: image/gif

- Content-Disposition - Оригиналната MIME спецификация описва само структурата на e-mail съобщенията без да описва начина на показването му. Този хедър е добаве в RFC 2183 и прави точно това. Възможните му стойности са:
  - *inline* - Съдържанието се показва директно в писмото.
  - *attachment* - Прикачените файлове не се показват автоматично с текста и се изисква допълнително действие от страна на потребителя, за да ги отвори.

- Content-Transfer-Encoding - Позволява изпращането на бинарни данни във формат, различен от ASCII символи. Възможностите са:
  - 7-bit - ASCII символи, до 998 байта (октети) на ред.
  - 8-bit - до 998 байта (октети) на ред.
  - quoted-printable
  - base64
  - binary - всякаква поредица от байтове.
- Content-ID - уникален идентификатор.

### Примерно писмо
<cite>
MIME-Version: 1.0 <br>
Content-Type: multipart/mixed; boundary=frontier <br>
From: Hristo Gatsinski \<gatsinski@tu-sofia.bg> <br>
To: Ivan Ivanov \<ivanov@tu-sofia.bg> <br>
Subject: "Тема на примерното писмо" <br>
<br>
\--frontier <br>
Content-Type: text/plain <br>
<br>
Съдържание на писмото. <br>
<br>
\--frontier <br>
Content-Type: application/octet-stream <br>
Content-Transfer-Encoding: base64 <br>
<br>
PGh0bWw+CiAgPGhlYWQ+CiAgPC9oZWFkPgogIDxib2R5PgogICAgPHA+VGhpcyBpcyB0aGUg
Ym9keSBvZiB0aGUgbWVzc2FnZS48L3A+CiAgPC9ib2R5Pgo8L2h0bWw+Cg== <br>
\--frontier\-- <br>
</cite>
