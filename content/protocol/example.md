---
title: "Примерна SMTP сесия"
name: "example"
date: 2017-12-14T22:05:23+02:00
draft: false
order: 4
---

R: 220 mgate.tu-sofia.bg EG4000/SMtp Ready

S: HELO tu-sofia.bg

R: 250 Requieted mail action okey, completed

S: MAIL FROM: petar@tu-sofia.bg

S: 250 OK

S: RCPT TO: georgi@gmail.com

R: 550 No such user here

S: RCPT TO: dimitar@tu-sofia.bg

R: 250 OK

S: DATA

R: 354 Start mail input ; end with <CRLF>.<CRLF>

S: From: Petar Ivanov

S: Subject: The Next Meeing of the Board

S: To: Ivan@tu-sofia.bg

S:

S: Срещата ни ще се състои следващата седмица

S: в сряда от 15:00 ч.

S:             Петър.

S:

R: 250 OK

S: QUIT

R: 221 Closing connection


Писмото ще бъде получено от Ivan и Dimitar, но не и от Georgi, поради грешен E-mail адрес.
