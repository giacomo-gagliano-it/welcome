# Cambiare users fra un push e l'altro.

vorrei pushare un cambiamento
ho chiusto tutte le pagine vscode
sono uscito da tutti gli account
sono entrato solo in giacomo-gagliano-it
ho configurato come git global user `user2`
ho configurato come git local user `user2`
ho aggiunto id_giacomo-gagliano-it in etc/ssh/ssh_config.
ho aggiunto id_giacomo-gagliano-it in ~/.ssh/config
ho tolto id_giacomo-gagliano-it in ~/.ssh/config
ho fatto `ssh-add -l` ed era vuoto
ho aggiunto la chiave con `ssh-add id_giacomo-gagliano-it`
ho provato a fare push e ha funzionato
ok, ho aggiunto la chiave all'agent ed ora funziona

ho provato a fare un cambiamento su zion, è riuscito a fare il commit, ma è con user giacomo-gagliano-it
ho configurato come git global user `user1`
ho fatto un cambiamento a zaion monorepo come `user1`
ho committato come `user1`
ho fatto push e mi ha dato errore non puoi pushare come `user2` (sta cercando di pushare come `user2`)

> a questo punto la cosa sembra che sia dovuta alla chiave aggiunta al ssh agent
> provo 
> - [x] aggiungere la chiave giusta
> - [ ] se non va tolgo la chiave `user2` e metto la chiave `user1`

ha funzionato semplicemente aggiungendo la chiave all ssh agent, almeno sembrerebbe.
e invece ho provato a pushare i cambiamenti a questo file e me lo ha impedito, eppure la chiave è presente.

> provo a
> - reimpostare come global gagliano-it

non ha funzionato

> pero ho provato a fare `ssh-add -D` cancellando tutte le chiavi nellagent, e poi ho fatto `ssh-add user2`. e ha funzionato

ora pusho questo e riprovo con zaion

prima pero provo a cambiare lo user globale di git

> ha funzionato, quindi ora posso provare con zaion

ho provato a cancellare il remote e mi dava errore
ho aggiunto `user1` al ssh agent e ha funzionato

ha funzionato correttamente ora vediamo se funziona ancora qui

> ho provato e non ha funzionato

quindi ora provo a fare come prima, cancello ssh agent e metto la chiave di `user2`

> effettivamente ha funzionato sta volta, quindi, non si sa come mai, ma se ci sono due chiavi e lo si carica in quello che è impostato come global non da problemi.
> mentre se si tratta di spingere sullo user che è solo in locale sembrerebbe che abbia bisogno che la chiave sia una sola.