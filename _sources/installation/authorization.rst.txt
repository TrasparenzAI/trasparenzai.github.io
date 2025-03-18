Autorizzazione
==============

L'accesso all'interfaccia web è condizionato dalla presenza o meno di 
determinati ruoli nel token JWT fornito dal sistema di autenticazione.
I ruoli attualmente previsti sono:

  - ROLE_USER
  - ROLE_ADMIN
  - ROLE_SUPERUSER

Le funzionalità mostrate nell'interfaccia web cambiano in funzione del ruolo
dell'utente, è quindi necessario attribuire nel Identity Provider OAuth2 il
ruolo desiderato ai propri utenti.
