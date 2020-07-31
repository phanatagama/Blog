---
layout: post
published: true
title: Tinder Auto Swipe
date: '2020-06-02'
image: /img/Automate/tinder-logo.png
---
Implementasi javascript programming for automate @ **#3*.

## Automasi Swipe Tinder

Script ini hanya modifikasi `perbaikan` dari script yang sebelumnya sudah tidak work
Penggunaan automasi tidak berjalan ketika jumlah swipe harian sudah habis. Upgrade Akun tindermu agar unlimited swipe

![1](/img/Automate/tinder.png)



Berikut kode telah saya perbaiki:

```
function hasBlacklistKeywords(bio) {
		var blacklist = [
			'ladyboy',
			'lady boy',
			'not a lady',
			'not lady',
			'not a girl',
			'not girl',
			'trans',
			'shemale',
			'chubby',
			//' lb ',
		];

		for (item of blacklist) {
				if(bio.toLowerCase().indexOf(item) !== -1) {
					console.log('skipping profile, matched blacklist keyword ' + item);
					return true;
				}
		}

		return false;
}

function hasValidProfile() {
		var bioClassName = 'profileCard__bio';
		try {
			var bio = document.getElementsByClassName(bioClassName)[0].textContent;
			console.log(bio);
			return !hasBlacklistKeywords(bio);
		} catch (e) {
			// console.log(e);
			return true; // possible empty bio
		}
		return false;
}

function checkTinder() {
	var base = "https://tinder.com/";
	return window.location.href.startsWith(base + "app/recs") || window.location.href.startsWith(base + "app/matches");
}

// prevent async execution
function pause(milliseconds) {
	var dt = new Date();
	while ((new Date()) - dt <= milliseconds) { /* Do nothing */ }
}

function trickTinder() {

	var infoClassName = 'recCard__info';
	var dislike = document.getElementsByClassName("button")[0];
	var like = document.getElementsByClassName("button")[3];

	// Open profile bio
	var info = document.getElementsByClassName(infoClassName)[0];
	if(info) {
			info.click();
	}
	pause(600);

	// Like or deslike depending on validation
	if(hasValidProfile()) {
			like.click();
	} else {
			dislike.click();
	}

	// If reached max likes per day then show modal and get it's content...
	// Check if there is any subscription button...
	if (document.getElementsByClassName('productButton__subscriptionButton').length > 0) {
		// We get the counter thing
		var hms = document.getElementsByClassName('Fz($ml)')[0].textContent;
		// Split it at the colons
		var a = hms.split(':');
		// Minutes are worth 60 seconds. Hours are worth 60 minutes. 1 second = 1kmilliseconds.
		// Genius... rocket science...
		var seconds = (+a[0]) * 6 * 6 + (+a[1]) * 6 + (+a[2])

		return seconds * 100;
	}
}

function checkOkCupid() {
	return window.location.href.startsWith("https://www.okcupid.com/doubletake");
}
function trickOkCupid() {
	// Press the like button
	document.getElementsByClassName('cardactions-action--like')[0].click();
}

// There is a lot more fun that can be achieved
// Need to add socket puppetry (VPNs solutions? several accounts?) - :D
// TODO: Need to accept automatically permissions except for
// TODO: Need to add ANN for fake pics
// TODO: Need to add RNN for fake messages

function getRandomPeriod() {
	return Math.round(Math.random() * (2000 - 5)) + 5;
}

(function loopSasori() {
	// A random period between 500ms and 2secs
	var randomPeriod = getRandomPeriod();
	setTimeout(function() {
		randomPeriod = undefined;
		if (checkTinder()) {
			var delay	= trickTinder();
			if (delay) {
				console.log('Too many likes for now, have to wait: ' + delay + ' ms');
				randomPeriod = delay;
			}
		}
		if (checkOkCupid()) {
			trickOkCupid();
		}
		if (!randomPeriod) {
			loopSasori();
		}
		else {
			setTimeout(loopSasori, randomPeriod);
		}
	}, randomPeriod);
}());
```

Cara menggunakan script diatas yaitu dengan memasukkannya pada console inspector browser.
Jangan lupa untuk mengganti isi blacklist sesuai selera.
Refresh halaman jika ingin berhenti swipe.
