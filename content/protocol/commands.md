---
title: "Команди в SMTP"
name: "smtp-commands"
date: 2017-12-14T21:38:50+02:00
draft: false
order: 3
---

Командите в SMTP представляват ASCII символни низове, завършващи в последователността <CRLF> (край на ред). Те се представят чрез кодове от 4 букви и имат до един аргумент с променлива дължина. Краят на командата и началото на аргумента се обозначава със <SP> (празен интервал).

Основни команди в протокола:

* <a href="#helo">**HELO**</a> <адрес на изпращач>
* <a href="#mail">**MAIL**</a> <обратен път>
* <a href="#rcpt">**RCPT**</a> <прав път>
* <a href="#data">**DATA**</a>
* <a href="#rset">**RSET**</a>
* <a href="#help">**HELP**</a> [<код на команда>]
* <a href="#noop">**NOOP**</a>
* <a href="#quit">**QUIT**</a>


## Описание на командите

* <span id="helo">**HELO**</span> <адрес на изпращач>
Служи за идентификация на SMTP изпращача пред SMTP получателя. Аргументът съдържа интернет адреса на системата SMTP изпращач.

* <span id="mail">**MAIL**</span> <обратен път>
Инициализира транзакция за обмен на писмо, което ще бъде изпратено до една или няколко потребителски пощенски кутии. Обратният път служи за уведомяване на подателя на писмото, в случай на възникване на грешка в процеса на доставянето му.

* <span id="rcpt">**RCPT**</span> <прав път>
Указва крайния получател на писмото. Ако писмото трябва да бъде доставено до множество плучатели, командата се използва многократно.

* <span id="data">**DATA**</span>
Определя началото на изпращане на писмото. При получаване на тази команда SMTP получателя изпраща положителен отговор и тълкува слеващите приети редове на съдържание на писмото.
Краят на писмото се определя от ред, съдържащ "<CRLF>.<CRLF>".
При получаването му SMTP получателят изпраща положителен отговор. С цел съхраняване на прозрачността на данните от писмото, се спазва следната процедура.

    * Преди да се изпрати поредния ред от писмото SMTP изпращачът анализира първият му знак. Ако този знак е точка, тя бива дублирана.
    * SMTP получателят анализира получените редове. Ако първият символ е точка и редът не съдържа други символи, тове е индикатор за край на писмото. Ако първият символ е точка и редът съдържа други символи, точката бива премахната.

* <span id="rset">**RSET**</span>
Прекратява изпълнението на текущата транзакция.

* <span id="help">**HELP**</span> [<код на команда>]
Командата изисква SMTP получателят да върне помощна информация за заявената команда. Ако аргументът липсва, се връща информация за всички команди, които SMTP получателят може да изпълни.

* <span id="noop">**NOOP**</span>
Командата не предизвиква никакви действия. SMTP получателят връща положителен отговор ОК.

* <span id="quit">**QUIT**</span>
Командата казва на SMTP получателят да прекрати TCP връзката.


## Ограничения в реда на извикване на командите

* Първата команда от всяка сесия трябва да бъде *HELO*.
* Командите *NOOP* и *HELP* могат да се използват по всяко време на сесията.
* Командата *MAIL FROM* инициализира транзакция. В рамките на една транзакция могат да бъдат издавани една или няколко команди *RCPT* и една команда *DATA*.
* Текущата транцакция може да бъде анулирана чрез командата *RSET*. Всяка сесия може да съдържа 0 или множество транзакции.
* Последна в сесията се издава командата *QUIT*.
