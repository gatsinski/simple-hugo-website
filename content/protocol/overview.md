---
title: "Общ преглед"
name: "overview"
date: 2017-12-10T11:16:40+02:00
draft: false
order: 1
---

**Simple Mail Transfer Protocol** или просто SMTP е интернет стандарт за пренос на електронна поща (email) от приложния слой (Application Layer) на OSI модела. Описан е за пръв път от
<a href="https://tools.ietf.org/html/rfc821" target="_blank">*RFC 821*</a> през 1982, а последното му обновяване става през 2008 г. с добавянето на *Extended SMTP* (Разширен SMTP) от
<a href="https://tools.ietf.org/html/rfc5321" target="_blank">*RFC 5321*</a>. Разширената версия на протокола е най-разпространената в днешно време.

Макар на потребителско ниво обикновено протокола да се използва само за изпращане на съобщения, докато за получаване се предпочитат протоколите <abbr title="Internet Message Access Protocol">IMAP</abbr> и <abbr title="Post Office Protocoll">POP3</abbr>, повечето пощенски сървъри и други услуги за пренос на съобщения използват SMTP както за изпращане, така и за получаване на съобщения.

SMTP комуникацията между пощенските сървъри използва <abbr title="Transmission Control Protocol">TCP</abbr> протокола през порт 25. Пощенските клиенти от друга страна, често подават изходящи писма на порт 587. Въпреки че е изваден от стандарта, някои доставчици на пощенски услуги все още позволяват да се използва и порт 465 за същата цел.

SMTP връзки, защитени с <abbr title="Transport Layer Security">TLS</abbr>, са известни още като <abbr title="Simple Mail Transfer Protocol Secure">SMTPS</abbr>.

<img align="right" alt="Рисунка на пътуващ пощенски плик" src="/simple-hugo-website/images/mail-drawing.png">

Въпреки че някои частни системи, като Microsoft Exchange и IBM Notes, и уебмейл системи, като Outlook, GMail и Yahoo! Mail, използват свои собствени нестандартни протоколи за достъп до пощенските кутии на своите собствени сървъри, всички използват SMTP, когато изпращат или получават съобщения от други системи.
