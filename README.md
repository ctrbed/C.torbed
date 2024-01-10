From kloecker at kde.org  Mon Jan  1 21:10:01 2024
From: kloecker at kde.org (Ingo =?ISO-8859-1?Q?Kl=F6cker?=)
Date: Mon, 01 Jan 2024 21:10:01 +0100
Subject: gpg --card-status
In-Reply-To: <ZZMTiJomLceJyNuN@c720-1400094>
References: <CA+m_8J0Mmhzae5Oh_ybEMG+cRoaD5eDZqqno_AfFwCoNWnODLg@mail.gmail.com>
 <12356199.O9o76ZdvQC@daneel> <ZZMTiJomLceJyNuN@c720-1400094>
Message-ID: <2726234.mvXUDI8C0e@daneel>

On Montag, 1. Januar 2024 20:33:28 CET Matthias Apitz wrote:
> It seems from the man page that only '#' is documented:

Must be an older version. The manual page of GnuPG 2.4.3 reads:

       ?K     List  the  specified  secret keys.  If no keys are specified, then 
all known secret keys are listed.  A # after the initial tags sec or ssb means 
that the secret key or subkey is currently not usable.  We also say that this 
key has been taken offline (for example, a primary key can be taken offline by 
exporting the key using  the  command  ??export?secret?subkeys).  A > after 
these tags indicate that the key is stored on a smartcard.  See also 
??list?keys.

Regards,
Ingo
-------------- next part --------------
A non-text attachment was scrubbed...
Name: signature.asc
Type: application/pgp-signature
Size: 228 bytes
Desc: This is a digitally signed message part.
URL: <https://lists.gnupg.org/pipermail/gnupg-users/attachments/20240101/f120a2e2/attachment.sig>

From guru at unixarea.de  Mon Jan  1 20:33:28 2024
From: guru at unixarea.de (Matthias Apitz)
Date: Mon, 1 Jan 2024 20:33:28 +0100
Subject: gpg --card-status
In-Reply-To: <12356199.O9o76ZdvQC@daneel>
References: <CA+m_8J0Mmhzae5Oh_ybEMG+cRoaD5eDZqqno_AfFwCoNWnODLg@mail.gmail.com>
 <12356199.O9o76ZdvQC@daneel>
Message-ID: <ZZMTiJomLceJyNuN@c720-1400094>

El d?a domingo, diciembre 31, 2023 a las 05:34:42p. m. +0100, Ingo Kl?cker escribi?:

> On Samstag, 30. Dezember 2023 23:30:39 CET Felix E. Klee wrote:
> > Line 25: ?sec>? means secret primary key. Where does the key ID come
> > from? Is it read from the card? Or it read from the public key ring on
> > disk?
> > 
> > Line 27: ?ssb>? means secret sub key.
> > 
> > Line 29: ?ssb#? means secret sub key, but without the matching secret
> > key on the card. This I just learned from Ingo Kl?cker in another
> > thread.
> 
> The meaning of ">" and "#" is documented in the description of the command
> `--list-secret-keys` in the manual page of gpg.
> 
> Regards,
> Ingo

It seems from the man page that only '#' is documented:

man gpg
...
       --list-secret-keys

       -K     List all keys from the secret keyrings, or just the ones given
              on the command line. A # after the letters sec means that the
              secret key is not usable (for example, if it was created via
              --export-secret-subkeys).

What does '>' means?

Thanks

	matthias

-- 
Matthias Apitz, ? guru at unixarea.de, http://www.unixarea.de/ +49-176-38902045
Public GnuPG key: http://www.unixarea.de/key.pub

I am not at war with Russia.
? ?? ???? ? ???????.
Ich bin nicht im Krieg mit Russland.


From johndoe65534 at mail.com  Tue Jan  2 09:40:20 2024
From: johndoe65534 at mail.com (john doe)
Date: Tue, 2 Jan 2024 09:40:20 +0100
Subject: OT: Best way to send e-mails to a recipient that does know encryption
Message-ID: <d25682ef-d8a1-4c59-adb1-e7b17c0d5f1d@mail.com>

Hi,

I need to send personal infos to a recipient who has no idea what
encryption is nor is able to decrypt  an encrypted e-mail.

I do not want to use Gmail to send that kind of informations and I'm
comtemplating using posteo.de.

Is this any better?

In other words, how do you use  e-mails with a recipient that should be
able to open and reply to e-mails as usual.

Sorry for being OT.

--
John Doe


From guru at unixarea.de  Tue Jan  2 12:44:27 2024
From: guru at unixarea.de (Matthias Apitz)
Date: Tue, 2 Jan 2024 12:44:27 +0100
Subject: gpg --card-status
In-Reply-To: <2726234.mvXUDI8C0e@daneel>
References: <CA+m_8J0Mmhzae5Oh_ybEMG+cRoaD5eDZqqno_AfFwCoNWnODLg@mail.gmail.com>
 <12356199.O9o76ZdvQC@daneel> <ZZMTiJomLceJyNuN@c720-1400094>
 <2726234.mvXUDI8C0e@daneel>
Message-ID: <ZZP3G8WRHlHSQttQ@c720-1400094>

El d?a lunes, enero 01, 2024 a las 09:10:01p. m. +0100, Ingo Kl?cker escribi?:

> On Montag, 1. Januar 2024 20:33:28 CET Matthias Apitz wrote:
> > It seems from the man page that only '#' is documented:
> 
> Must be an older version. The manual page of GnuPG 2.4.3 reads:

You are correct:

$ gpg --version | grep ^gpg
gpg (GnuPG) 1.4.23
$ man gpg | col -b | grep -A5 -- -K
       -K     List all keys from the secret keyrings, or just the ones given
	      on the command line. A # after the letters sec means that the
	      secret key is not usable (for example, if it was created via
	      --export-secret-subkeys).


$ gpg2 --version | grep ^gpg
gpg (GnuPG) 2.4.3
$ man gpg2 | col -b | grep -A5 -- -K
       -K     List the specified secret keys.  If no keys are specified, then
	      all known secret keys are listed.  A # after the initial tags
	      sec or ssb means that the secret key or subkey is currently not
	      usable.  We also say that this key has been taken offline (for
	      example, a primary key can be taken offline by exporting the key
	      using the command --export-secret-subkeys).  A > after these
	      ...

Thanks

	matthias

-- 
Matthias Apitz, ? guru at unixarea.de, http://www.unixarea.de/ +49-176-38902045
Public GnuPG key: http://www.unixarea.de/key.pub

I am not at war with Russia.
? ?? ???? ? ???????.
Ich bin nicht im Krieg mit Russland.


From lists at lrose.de  Tue Jan  2 12:16:15 2024
From: lists at lrose.de (LuKaRo)
Date: Tue, 2 Jan 2024 12:16:15 +0100
Subject: OT: Best way to send e-mails to a recipient that does know
 encryption
In-Reply-To: <d25682ef-d8a1-4c59-adb1-e7b17c0d5f1d@mail.com>
References: <d25682ef-d8a1-4c59-adb1-e7b17c0d5f1d@mail.com>
Message-ID: <e5851d47-951e-47e5-9f34-51ca680db9c2@lrose.de>

> I do not want to use Gmail to send that kind of informations and I'm
> comtemplating using posteo.de.
>
> Is this any better?

I'd argue of course it's better. Google openly admits reading your 
e-mail, so other mail providers that respect your privacy should be 
preferred. I particularly like posteo.de, because the 1?/month fee is 
still very cheap but makes clear that they have a different business 
model that doesn't involve customer data. Furthermore, they deploy a 
very sophisticated solution that makes it technically impossible to 
match payment data or IP addresses to mailboxes, and even fought (and 
won!) a lawsuit against the German authorities that wanted to force 
posteo to hand out customer data (which they don't even collect).

However, while this will surely be an improvement over providers like 
Google, it doesn't solve the encryption problem. While providers like 
posteo make it easy for laypeople to use encryption, for example by 
providing good instructions and supporting gpg encryption in their 
webclient, you'd probably still need to help a layperson in setting up 
their gpg keys, either in thunderbird or in the webclient of a provider 
supporting this. So if the person is willing to try encryption, you're 
probably best off by helping them doing it before sending your personal 
information.

Hope that helps a bit,

lukaro



From kloecker at kde.org  Tue Jan  2 15:23:28 2024
From: kloecker at kde.org (Ingo =?ISO-8859-1?Q?Kl=F6cker?=)
Date: Tue, 02 Jan 2024 15:23:28 +0100
Subject: OT: Best way to send e-mails to a recipient that does know
 encryption
In-Reply-To: <e5851d47-951e-47e5-9f34-51ca680db9c2@lrose.de>
References: <d25682ef-d8a1-4c59-adb1-e7b17c0d5f1d@mail.com>
 <e5851d47-951e-47e5-9f34-51ca680db9c2@lrose.de>
Message-ID: <2172977.irdbgypaU6@daneel>

On Dienstag, 2. Januar 2024 12:16:15 CET LuKaRo wrote:
> > I do not want to use Gmail to send that kind of informations and I'm
> > comtemplating using posteo.de.
> > 
> > Is this any better?
> 
> I'd argue of course it's better. Google openly admits reading your
> e-mail, so other mail providers that respect your privacy should be
> preferred. I particularly like posteo.de, because the 1?/month fee is
> still very cheap but makes clear that they have a different business
> model that doesn't involve customer data. Furthermore, they deploy a
> very sophisticated solution that makes it technically impossible to
> match payment data or IP addresses to mailboxes, and even fought (and
> won!) a lawsuit against the German authorities that wanted to force
> posteo to hand out customer data (which they don't even collect).

Posteo will release data to authorities if they are forced to do so by a 
judicial order. See their transparency reports for details:
https://posteo.de/en/site/transparency_report

I'm still using Posteo.

Regards,
Ingo
-------------- next part --------------
A non-text attachment was scrubbed...
Name: signature.asc
Type: application/pgp-signature
Size: 228 bytes
Desc: This is a digitally signed message part.
URL: <https://lists.gnupg.org/pipermail/gnupg-users/attachments/20240102/1dd94b56/attachment-0001.sig>

From fa-ml at ariis.it  Tue Jan  2 14:18:47 2024
From: fa-ml at ariis.it (Francesco Ariis)
Date: Tue, 2 Jan 2024 14:18:47 +0100
Subject: OT: Best way to send e-mails to a recipient that does know
 encryption
In-Reply-To: <d25682ef-d8a1-4c59-adb1-e7b17c0d5f1d@mail.com>
References: <d25682ef-d8a1-4c59-adb1-e7b17c0d5f1d@mail.com>
Message-ID: <ZZQNN2VeGG6bia0U@x270.casa>

Il 02 gennaio 2024 alle 09:40 john doe via Gnupg-users ha scritto:
> In other words, how do you use  e-mails with a recipient that should be
> able to open and reply to e-mails as usual.

If email is not a strict requirement, two Matrix can be set up
to have an encrypted conversation, same with XMPP
?F



From felix.klee at inka.de  Tue Jan  2 23:06:59 2024
From: felix.klee at inka.de (Felix E. Klee)
Date: Tue, 2 Jan 2024 23:06:59 +0100
Subject: gpg --card-status
In-Reply-To: <CA+m_8J0Mmhzae5Oh_ybEMG+cRoaD5eDZqqno_AfFwCoNWnODLg@mail.gmail.com>
References: <CA+m_8J0Mmhzae5Oh_ybEMG+cRoaD5eDZqqno_AfFwCoNWnODLg@mail.gmail.com>
Message-ID: <CA+m_8J3QdOhMvAgVRiOt_A+VL4Y1FxTSrwE09m-0MJ5oqwY7cQ@mail.gmail.com>

On Sat, Dec 30, 2023 at 11:30?PM Felix E. Klee <felix.klee at inka.de> wrote:
> Example output with line numbers:
>
>     01 Reader ...........: Yubico YubiKey CCID 00 00
>     02 Application ID ...: D2760001240103040006186980150000
>     03 Application type .: OpenPGP
>     04 Version ..........: 3.4
>     05 Manufacturer .....: Yubico
>     06 Serial number ....: 18698015
>     07 Name of cardholder: [not set]
>     08 Language prefs ...: [not set]
>     09 Salutation .......:
>     10 URL of public key : [not set]
>     11 Login data .......: [not set]
>     12 Signature PIN ....: not forced
>     13 Key attributes ...: rsa4096 rsa4096 rsa4096
>     14 Max. PIN lengths .: 127 127 127
>     15 PIN retry counter : 3 0 3
>     16 Signature counter : 0
>     17 KDF setting ......: off
>     18 Signature key ....: 7A0F E73D DB74 4F0F 9734  1DA7 1BE3 49D1 1B6E
>        D589
>     19       created ....: 2023-06-29 03:50:43
>     20 Encryption key....: DBBD 3239 D0F1 4326 808D  FC8F 7CC0 2D68 D2E3
>        1736
>     21       created ....: 2023-06-29 03:50:43
>     22 Authentication key: 7A0F E73D DB74 4F0F 9734  1DA7 1BE3 49D1 1B6E
>        D589
>     23       created ....: 2023-06-29 03:50:43
>     24 General key info..: pub  rsa4096/1BE349D11B6ED589 2023-06-29
>        Felix E. Klee (YubiKey) <yubikey at f76.eu>
>     25 sec>  rsa4096/1BE349D11B6ED589  created: 2023-06-29  expires:
>        never
>     26                                 card-no: 0006 18698015
>     27 ssb>  rsa4096/7CC02D68D2E31736  created: 2023-06-29  expires:
>        never
>     28                                 card-no: 0006 18698015
>     29 ssb#  rsa4096/32B106F6877CC64B  created: 2023-11-22  expires:
>        never

Thanks for all the input! My current state of knowledge is:

  * Lines 18, 20, 22: Fingerprints identifying the secret keys stored on
    the card.

    A fingerprint is an SHA-1 hash of: corresponding public key + some
    meta data

    The fingerprints displayed on these lines are stored on the card.

  * Lines 25, 27, 29: Information about availability of secret keys on
    the card.

    The numbers are long key IDs. A long key ID is the last 16
    characters of a fingerprint.

    The fingerprints displayed on these lines are generated from the
    public keys stored on disk.

    Here:

      - sec: Secret primary key

      - ssb: Secret sub key

      - >: Secret key is available on the card

      - #: Secret key is missing from the card

For a summary concerning how the fingerprints are calculated, I found:

https://blog.djoproject.net/2020/05/03/main-differences-between-a-gnupg-fingerprint-a-ssh-fingerprint-and-a-keygrip/

Please correct me where I?m wrong!


From vedaal at nym.hush.com  Wed Jan  3 05:10:55 2024
From: vedaal at nym.hush.com (vedaal at nym.hush.com)
Date: Tue, 02 Jan 2024 23:10:55 -0500
Subject: OT: Best way to send e-mails to a recipient that does know
 encryption
In-Reply-To: <2172977.irdbgypaU6@daneel>
References: <d25682ef-d8a1-4c59-adb1-e7b17c0d5f1d@mail.com>
 <e5851d47-951e-47e5-9f34-51ca680db9c2@lrose.de> <2172977.irdbgypaU6@daneel> 
Message-ID: <a6497b6aaf6290391f38aa0dee02dc87a9436354aba9636c@smtp.hushmail.com>



On 1/2/2024 at 9:26 AM, "Ingo Kl?cker" <kloecker at kde.org> wrote:

>Posteo will release data to authorities if they are forced to do 
>so by a 
>judicial order. See their transparency reports for details:
>https://posteo.de/en/site/transparency_report
>
>I'm still using Posteo.

=====

Another option is Hushmail.

It allows to send encrypted mail to someone who has no encryption experience and to any email address.

The Receiver agrees on a passphrase with the Sender, and the Sender sends the encrypted email.

The Receiver gets a notice in whatever email he/she is using, with a link to a site on the hushmail server.

The Receiver clicks on a link, and Hushmail requests  a passphrase.  Only 3 attempts are allowed.  The message is erased on the 4th try.

The message is also erased after 72 hours from the time it is sent.  If the passphrase is correct, it displays the plaintext of the message.

Again, if you are suspected of being a terrorist or a human trafficker, and Law Enforcement gets a convincing order, they will release your information.

They are based in Canada.   Price is 49 US$ / year.   Allows for unlimited aliases, (that haven't already been taken).

If anyone wants to try out the encryption, please send me an email, and tell me what you want your passphrase to be.


vedaal



From felix.klee at inka.de  Fri Jan  5 10:07:07 2024
From: felix.klee at inka.de (Felix E. Klee)
Date: Fri, 5 Jan 2024 10:07:07 +0100
Subject: Cannot export SSH public key
In-Reply-To: <CA+m_8J0w_EcpJ+ai7sUVCfncP6br_4cF8aiyLJiKRgjR1z8p8Q@mail.gmail.com>
References: <CA+m_8J0LXKtqmg+PRNpGbe8J+wHvKCg_tCcnQApDAencXAYA+Q@mail.gmail.com>
 <12329793.O9o76ZdvQC@daneel>
 <CA+m_8J3_a7Gnx5L-2xN8GitO1SWSc+EE983PSF1QYmz=cy+kjA@mail.gmail.com>
 <874jhedjz4.fsf@jacob.g10code.de>
 <CA+m_8J0LiCgV=rykop4tahd1Q0udumj-17zCgJmn0bO+Zg31xQ@mail.gmail.com>
 <2f37ba49338c0858e9dfbb6f8396d202d2091ac0.camel@posteo.de>
 <CA+m_8J0w_EcpJ+ai7sUVCfncP6br_4cF8aiyLJiKRgjR1z8p8Q@mail.gmail.com>
Message-ID: <CA+m_8J0k4hKq2HOmhGx5D=yS5JT6tcVKbpMZTbDCijqTinDhsw@mail.gmail.com>

On Fri, Nov 24, 2023 at 9:09?AM Felix E. Klee <felix.klee at inka.de> wrote:
> In addition, I need:
>
>     gpg-connect-agent updatestartuptty /bye

or otherwise, I get no PIN entry dialog / prompt


From wk at gnupg.org  Fri Jan  5 14:42:58 2024
From: wk at gnupg.org (Werner Koch)
Date: Fri, 05 Jan 2024 14:42:58 +0100
Subject: Cannot export SSH public key
In-Reply-To: <CA+m_8J0k4hKq2HOmhGx5D=yS5JT6tcVKbpMZTbDCijqTinDhsw@mail.gmail.com>
 (Felix E. Klee's message of "Fri, 5 Jan 2024 10:07:07 +0100")
References: <CA+m_8J0LXKtqmg+PRNpGbe8J+wHvKCg_tCcnQApDAencXAYA+Q@mail.gmail.com>
 <12329793.O9o76ZdvQC@daneel>
 <CA+m_8J3_a7Gnx5L-2xN8GitO1SWSc+EE983PSF1QYmz=cy+kjA@mail.gmail.com>
 <874jhedjz4.fsf@jacob.g10code.de>
 <CA+m_8J0LiCgV=rykop4tahd1Q0udumj-17zCgJmn0bO+Zg31xQ@mail.gmail.com>
 <2f37ba49338c0858e9dfbb6f8396d202d2091ac0.camel@posteo.de>
 <CA+m_8J0w_EcpJ+ai7sUVCfncP6br_4cF8aiyLJiKRgjR1z8p8Q@mail.gmail.com>
 <CA+m_8J0k4hKq2HOmhGx5D=yS5JT6tcVKbpMZTbDCijqTinDhsw@mail.gmail.com>
Message-ID: <87o7dz3nh9.fsf@jacob.g10code.de>

On Fri,  5 Jan 2024 10:07, Felix E. Klee said:

>>     gpg-connect-agent updatestartuptty /bye
>
> or otherwise, I get no PIN entry dialog / prompt

That is right.  The ssh-agent protocol has no means to tell the
ssh-agent or gpg-agent some important environment cariabales, like the
current tty or DISPLAY.  I can't remember what ssh-askpass (?) works but
for GnUPG, gpg-agent uses the tty/display from where it was launched if
it does not know anything else

updatestartuptty tells gpg-agent that it should assume that the
tty/display whenre gpg-connect-agent was run should be the new default.

Fixing this in the ssh-agent protocol would be easy and I actually
implemented this but did not found the time to keep on nagging them to
include my patch to pass arbitrary envvars over the ssh-agent protocol.

The gnupg part has long been implemented:
https://dev.gnupg.org/rG224e26cf7b67f22bb0140133eac6b4ad24f3b1b7 and
somewhere on the openssh ML one should find my patch.

I am so used to run the updatestartuptty that I don't even think about
this.  It is the first thing I do when I ssh into my laptop.


Shalom-Salam,

   Werner

-- 
The pioneers of a warless world are the youth that
refuse military service.             - A. Einstein
-------------- next part --------------
A non-text attachment was scrubbed...
Name: openpgp-digital-signature.asc
Type: application/pgp-signature
Size: 247 bytes
Desc: not available
URL: <https://lists.gnupg.org/pipermail/gnupg-users/attachments/20240105/6ab7d8e7/attachment.sig>

From ming at imkuang.com  Fri Jan  5 14:25:28 2024
From: ming at imkuang.com (Ming Kuang)
Date: Fri, 5 Jan 2024 21:25:28 +0800
Subject: typo in section 7.4.3 of the gpgme manual
Message-ID: <001501da3fda$a7cd7010$f7685030$@imkuang.com>

Hi,

I noticed a typo when reading the gpgme manual via "info gpgme" on my
Ubuntu 22.04 (libgpgme-dev 1.16.0-1.2ubuntu4.1)

It also exists in the latest HTML web reference manual (edition 1.23.2):
https://www.gnupg.org/documentation/manuals/gpgme/Setting-the-Sender.html

> The function gpgme_set_sender specifies the sender address for use in 
> sign and verify operations. address is expected to be the ?addr-spec? 
> part of an address but **my also be** a complete mailbox address, in
> ...
I think it should be "may also be" instead of "my also be" :)
-------------- next part --------------
A non-text attachment was scrubbed...
Name: openpgp-digital-signature.asc
Type: application/pgp-signature
Size: 834 bytes
Desc: not available
URL: <https://lists.gnupg.org/pipermail/gnupg-users/attachments/20240105/1b0ab117/attachment.sig>

From felix.klee at inka.de  Fri Jan  5 21:58:37 2024
From: felix.klee at inka.de (Felix E. Klee)
Date: Fri, 5 Jan 2024 21:58:37 +0100
Subject: Cannot export SSH public key
In-Reply-To: <87o7dz3nh9.fsf@jacob.g10code.de>
References: <CA+m_8J0LXKtqmg+PRNpGbe8J+wHvKCg_tCcnQApDAencXAYA+Q@mail.gmail.com>
 <12329793.O9o76ZdvQC@daneel>
 <CA+m_8J3_a7Gnx5L-2xN8GitO1SWSc+EE983PSF1QYmz=cy+kjA@mail.gmail.com>
 <874jhedjz4.fsf@jacob.g10code.de>
 <CA+m_8J0LiCgV=rykop4tahd1Q0udumj-17zCgJmn0bO+Zg31xQ@mail.gmail.com>
 <2f37ba49338c0858e9dfbb6f8396d202d2091ac0.camel@posteo.de>
 <CA+m_8J0w_EcpJ+ai7sUVCfncP6br_4cF8aiyLJiKRgjR1z8p8Q@mail.gmail.com>
 <CA+m_8J0k4hKq2HOmhGx5D=yS5JT6tcVKbpMZTbDCijqTinDhsw@mail.gmail.com>
 <87o7dz3nh9.fsf@jacob.g10code.de>
Message-ID: <CA+m_8J1NHUyhrjsM--=o8Py4QwBpczkUuGLoJ1DY6xTB0R1LOQ@mail.gmail.com>

On Fri, Jan 5, 2024 at 2:43?PM Werner Koch <wk at gnupg.org> wrote:
> That is right.  The ssh-agent protocol has no means to tell the
> ssh-agent or gpg-agent some important environment cariabales, like the
> current tty or DISPLAY.

Interesting, thanks for the look behind the scenes!

> I am so used to run the updatestartuptty that I don't even think about
> this. It is the first thing I do when I ssh into my laptop.

I have to do it twice, though, until it works. In my `~/.bashrc` I have:

    gpg-connect-agent updatestartuptty /bye

Right after logging in (auto login on Ubuntu / WSL 2), I get:

    gpg-connect-agent: no running gpg-agent - starting
    '/usr/bin/gpg-agent'
    gpg-connect-agent: waiting for the agent to come up ... (5s)
    gpg-connect-agent: connection to agent established

That looks good, but somehow it doesn?t work:

    $ ssh some_server
    sign_and_send_pubkey: signing failed for RSA "cardno:18 698 015"
    from agent: agent refused operation
    sign_and_send_pubkey: signing failed for RSA "(none)" from agent:
    agent refused operation
    felix at some_server: Permission denied (publickey).

After starting `tmux`, which runs `gpg-connect-agent` again, everything
works fine. I get the PIN entry dialog, and I can connect by SSH.

This is a non-issue, not really worth debugging. I start `tmux` every
time anyhow.

