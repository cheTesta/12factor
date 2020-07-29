## I. Codebase
### Una sola codebase sotto controllo di versione, tanti deploy

Un'app conforme alla metodologia twelve-factor è sempre sotto un sistema di controllo di versione, sia esso [Git](http://git-scm.com/), [Mercurial](https://www.mercurial-scm.org/), o [Subversion](http://subversion.apache.org/). Una copia della codebase è detta *code repository*, oppure più in breve *code repo* o *repo*.

Una *codebase* è quindi un singolo repository (in un sistema di revisione centralizzato come Subversion), oppure un set di repo che condividono una root commit (in un sistema di controllo decentralizzato come Git).

![Una codebase, N deployment](/images/codebase-deploys.png)

C'è sempre una relazione uno-ad-uno tra codebase e applicazione:

* Se ci sono più codebase, non si parla più di applicazione ma di sistema distribuito. Ogni componente in un sistema distribuito è un'applicazione, e ognuna di queste applicazioni può individualmente aderire alla metodologia twelve-factor.
* Se più applicazioni condividono lo stesso codice si ha una violazione del twelve-factor. La soluzione in questo caso richiede un refactoring del codice condiviso in librerie che possono così essere incluse tramite un [dependency manager](./dependencies).

Quindi: un'unica codebase per applicazione, ma comunque con tanti deployment della stessa app. Per *deploy* si intende un'istanza funzionante dell'applicazione. Può essere l'istanza del software in produzione, oppure una delle varie istanze in staging. Inoltre, un deploy può essere una delle copie possedute dai singoli sviluppatori nei rispettivi ambienti di sviluppo locale.

La codebase rimane sempre la stessa su tutti i deployment, anche se potrebbero essere attive diverse versioni nello stesso istante. Per esempio, uno sviluppatore che ha dei commit in più che non ha ancora distribuito in staging; contemporaneamente, lo staging ha dei commit non distribuiti in produzione. Nonostante ciò, tutti condividono la stessa codebase, nonostante la possibilità di avere più deploy della stessa app.
