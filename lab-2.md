## Pripremna pitanja

1. What is the _Address Resolution Protocol (ARP)_, and what is its role in a network?
    - ARP je komunikacijski protokol korišten za otkrivanje _link layer_ adrese, npr. MAC adrese, koja je vezana uz danu adresu _internet layera_, najčešće IPv4 adresu. ARP je zahtjev-odgovor protokol, odnosno njegove su poruke direktno enkapsulirane _link layer_ protokolom. Komunicira unutar jedne mreže, nikad preko više međusobno povezanih čvorova. ARP u suštini spaja promjenjivu IP adresu sa statičnom MAC adresom.
  
2. What is a _Man-in-the-Middle (MitM)_ attack, and how does ARP spoofing enable it?
   - _Man-in-the-Middle_ napad je tip cyber-napada u kojem se napadač "injektira" u komunikaciju između dvije strane, sluša što razmjenjuju i ima mogućnost promjene sadržaja poruka, bez znanja strana koje komuniciraju. ARP spoofing omogućava MitM napad tako što se napadač predstavi kao ciljani primatelj poruke odgovorom na ARP request i zatim prosljeđuje poruke koje primi stvarnom primatelju te na taj način stranke u komunikaciji nemaju pojma da su napadnute.

3. How does an attacker use ARP spoofing to intercept network traffic?
   - ARP spoofing omogućava MitM napad tako što napadač odgovori na ARP request koji šalje stranka (on se broadcasta cijeloj mreži) čime se pravi da je primatelj i zatim prosljeđuje poruke koje primi stvarnom primatelju. Na taj način stranke u komunikaciji ne znaju da su napadnute jer je komunikacija održana.
  
4. How is the _cookie_ used to derive the encryption/decryption key?
   - Tajni cookie je vrijednost koja se prosljeđuje derive_key funkciji koja zatim na temelju danog stringa (seeda) derivira enkripcijski/dekripcijski ključ modernom key derivation funkcijom scrypt.

5. What REST API request do you need to send to the _crypto oracle_ the secret cookie?
   - GET request (GET /arp/cookie)
  
6. How do you obtain the authentication token?
   - Izvršavanjem MitM napada i presretanjem komunikacije između _crypto oracle_ servera i računala arp_client. _Crypto oracle_ odgovara slanjem tokena u određenom formatu.
  
7. How do you use the authentication token to obtain the cookie?
   - Nakon što presretnemo autentifikacijski token možemo se autentificirati te poslati GET request na /arp/cookie i dobiti cookie

8. What encryption mode is used to encrypt the challenge in this lab?
   - CBC

9. What tool can you use to capture network traffic on a local network interface?
    - tcpdump
