# TGUserbot
![TGUserbot account manager](https://i.imgur.com/B6TUHyv.png)
![TGUserbot account manager](https://i.imgur.com/USK2Epe.png)
![TGUserbot](https://i.imgur.com/LKit3Ce.png)
Installazione
-------------
Automatica (Ubuntu/Debian)

	curl https://peppelg.github.io/tguserbot_installer.sh | sudo bash
	cd TGUserbot

Manuale:
Installa i pacchetti `git zip screen php php-mbstring php-xml php-gmp php-curl php-bcmath php-zip php-json php-cli`

	git clone https://github.com/peppelg/TGUserbot
	cd TGUserbot && rm -rf src
	./TGUserbot.phar
	
[Passare da TGUserbotV3 a TGUserbotV4](https://t.me/TGUserbotChannel/13)

Impostazioni
---------------
Impostazioni in settings.php

	bot_file - imposta la path del file bot.php
	language - imposta la lingua
	session - imposta il nome del file della sessione madeline
	cronjobs - attivare i cronjob?
	send_errors - invia errori in chat
	readmsg - legge i messaggi in chat privata
	always_online - mantiene lo stato in linea
	auto_reboot - se TGUserbot crasha si riavvia automaticamente
	multithread - abilita multithread
	send_data - aiuta a migliorare TGUserbot inviando alcuni dati (https://tguserbot.peppelg.space/privacy.txt)
	proxy - vedi https://github.com/peppelg/TGUserbot#proxy


Avvio
-----
	./TGUserbot.phar
Avvio in background:

	./TGUserbot.phar --background

Aggiornare Madeline
------------------
	Rimuovi il file `madeline.phar` e riavvia TGUserbot.
	
🌟 TGUserbot.phar sarà aggiornato automaticamente.


Multi account
-------------
Carica una sessione: `./TGUserbot.phar --session="nomesessione"`

Carica una sessione in background: `./TGUserbot.phar --session="nomesessione"` --background

🔥 Gestisci account: `./TGUserbot.phar accounts`

Variabili e funzioni
--------------------
Variabili

	$update - update ricevuto
	$msg - messaggio
	$chatID - id della chat
	$userID - id utente
	$msgid - id del messaggio
	$type - user, bot, group, supergroup, channel
	$name - nome dell'utente
	$username - username dell'utente
	$title - titolo della chat
	$chatusername - username della chat
	$cronjob - id cronjob
	$me - informazioni sull'utente


Funzioni

	sm(Chat, Message, Reply, ParseMode);

[Metodi MadelineProto](https://docs.madelineproto.xyz/API_docs/methods/)

Proxy
------
1. Proxy automatico: TGUserbot otterrà automaticamente un proxy e lo userà, aggiungi in settings.php ```'proxy' => 'auto'```
2. Manuale: Aggiungi in settings.php ```proxy => ['type' => 'socks5', 'ip' => 'ip del proxy', 'port' => 'porta del proxy', 'username' => 'username proxy', 'password' => 'password proxy']```. Per i proxy http sostituisci `socks5` con `http`. Puoi omettere username e password.

Cronjobs
---------
Crea un nuovo cronjob (tra un minuto):

	$cron->add('next minute', 'cronjobid');
	//oppure
	$cron->add(time()+60, 'cronjobid');

Cancella un cronjob:

	$cron->delete('cronjobid');

Cancella tutti i cronjob:

	$cron->delete();

Quando sarà il momento, verrà dichiarata la variabile `$cronjob`, potrai gestire tutto da bot.php.

Esempio (bot.php):

	if ($msg == 'Invia tra un minuto un messaggio a 🅱️eppe') {
	  $cron->add('next minute', 'messaggio a peppe');
	  sm($chatID, 'Ok! Tra un minuto invierò un messaggio a Peppe');
	}
	if ($cronjob == 'messaggio a peppe') {
	  sm('@peppelg1', 'Zao, kome stai¿¿');
	}

⚠️ I secondi non verrano considerati

Plugin
-------
Per installare un plugin crea una cartella chiamata `plugins` e metti dentro i plugin. Facile eh?

[Scarica un plugin di esempio](https://peppelg.github.io/tguserbotPlugin_memoryusage.php)


Creare un bot (non userbot) con TGUserbot
------------------------------------------
Avvia accountmanager.php, vai su Aggiungi account e scrivi il nome della sessione. Quando TGUserbot chiederà il numero di telefono, scrivi `bot` e poi il token del bot.

Supporto
--------
[Canale Telegram di TGUserbot](https://t.me/TGUserbotChannel)

[Gruppo Telegram di TGUserbot](https://t.me/joinchat/HIyPnk3GQ7525LpP62yIWA)

[Gruppo Telegram di peppelg](https://t.me/joinchat/AAAAAEHRBNZBqxOlwtwBaQ)

[Gruppo Telegram di MadelineProto](https://t.me/pwrtelegramgroupita)

[Gruppo Telegram di MadelineProto inglese](https://t.me/joinchat/Bgrajz6K-aJKu0IpGsLpBg)
