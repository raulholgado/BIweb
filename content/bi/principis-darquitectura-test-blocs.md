---
title: Principis d'arquitectura
description: prova
weight: '3'
Blocs:
  - contingut: >
      * Els nous sistemes i aplicacions es regiran pels principis de **cloud
      first** (i preferentment a **cloud públic**), **mobile first** (en el
      sentit de multidispositiu) i seran **data-centric**  (la dada com a actiu
      més important de l'organització)

      * A l'hora de construir sistemes d'informació, s'optarà preferentment per
      la construcció basada en *serveis administrats* (això és, operació inclosa
      en el servei). Això aplica tant:
        * als building blocks de desplegament: PaaS, CaaS, FaaS, SaaS per sobre de IaaS/VM
        * als serveis existents en els clouds de referència: serveis de notificacions, cues, CDN, storage, …, per sobre de solucions desenvolupades a mida
      * Ponderar sempre **tecnologia vs negoci**: la millor tecnologia no sempre
      és la millor solució per a l'organització → s'han de balancejar aspectes
      tecnològics, de govern, funcionals, organitzatius i econòmics
    titol: ' Principis estratègics'
  - contingut: >-
      * **Segregació de funcions/responsabilitats**: les aplicacions han d'estar
      estructuralment dividides en blocs independents per funcionalitats,
      processos de negoci o serveis, per tal d'evitar els monòlits → patró de
      microserveis:
        * Aquest principi és d'aplicació a totes les capes: la divisió lògica de les funcionalitats també s'hauria de correspondre a una divisió "física” en el desplegament → un servei, una base de dades <br /> <br />


      * La **presentació** (client/frontend) i el **backend/negoci** estaran
      **desacoblats**.

      * **Orientació a serveis**. Les aplicacions poden ser consumides
      externament o bé han d'integrar-se amb 3rs. Els backend han d'exposar la
      seva funcionalitat de negoci via serveis per facilitar-ho. Aquests serveis
      seran, a més, fàcilment integrables a l'API Gateway, per a ser securitzats
      i governats de manera centralitzada.

      * **Emmagatzema a la memòria cau tot allò que sigui possible**. Per
      fer-ho, utilitza la tecnologia que millor s'adapti tant a client (html5
      cache, localstorage , etc.) com a servidor (Redis, Varnish, Memcache,
      caché personalitzada, etc.)

      * Tingues present sempre la **compatibilitat cap a enrere dels teus
      serveis**: si exposes una API REST i actualitzes el teu servei, que sigui
      compatible amb versions anteriors per a evitar actualitzacions
      innecessàries als teus consumidors i d'aquesta manera poder evolucionar el
      servei lliurement.

      * Dissenya l'aplicació o servei tenint present els conceptes d'elasticitat
      (enlloc de per a suportar els pics de càrrega), d'alta disponibilitat,
      d'alta concurrència i zero downtime.

      * Pensa en la portabilitat de les aplicacions, això és, que es puguin
      moure amb facilitat d'un cloud privat a un cloud públic, per exemple.

      * A l'hora de dissenyar el teu sistema cal incorporar aspectes qualitatius
      al cicle de vida:
        * Proves per a verificar la qualitat del codi, el suport de càrrega o requisits no funcionals del sistema.
        * Documentació detallada del projecte (descripció d'arquitectura, document funcional, manual de desplegament, manual d'explotació, …).
        * Control de versions. El sistema en el seu conjunt ha de ser tractat com un producte amb les seves versions majors, menors, etc
        * Desplegament automatitzat, execució de proves automàtiques que verifiquin la instal·lació i integració contínua.
      * Si has d'emprar dades d'un altre sistema, millor consumeix-les via
      serveis. Les dades d'aquell sistema han de ser "l'única font de la
      veritat”

      * Delega les decisions d'autenticació en el proveïdor d'identitat de la
      UOC (IdP) utilitzant el protocol SAML. Les decisions d'autorització
      s'haurien de prendre en l'àmbit de l'aplicació, però preferiblent amb les
      dades proporcionades pel IdP.
    titol: Principis sobre el disseny d'aplicacions
  - contingut: >-
      * Utilitza la tecnologia que millor encaixi al cas d'ús, si cal combinant
      tecnologies, ja que en un mateix sistema en poden conviure diverses: per
      exemple, en dividir les aplicacions en serveis, no tots tenen perquè estar
      construïts en els mateixos llenguatges o utilitzar les mateixes bases de
      dades.

      * Els serveis (backend) exposaran el seu negoci preferentment mitjançant
      REST i en format JSON.

      * En el cas d'aplicacions web, la presentació estarà construïda amb
      tecnologies estàtiques (html5/javascript/css) i consumirà els serveis que
      li proporcioni el backend.

      * Davant solucions estàndards utilitzarem preferentment les tecnologies
      del Full de Ruta Tecnològic (en definició). Aquest fet no exclou que per a
      noves solucions es puguin utilitzar altres tecnologies, que eventualment
      passaran a formar-ne part.

      * Planifica i gestiona l'obsolescència tecnològica (sistemes operatius,
      middlewares, frameworks de desenvolupament, productes, ...): és una
      inversió que reduirà riscos
    titol: Principis sobre la tecnologia
  - contingut: >-
      * Cal tenir presents els costos d'infraestructura i el model de
      llicenciament requerits per a posar en marxa una solució ja que
      representen un cost recurrent.

      * Pensa en els costos i en la seva optimització:
        * Monitoritza els teus serveis per a identificar necessitats d'ampliació o reducció de recursos i poder ajustar els costos en conseqüència
        * Arquitectura/dissenya les càrregues de treball amb els costos en ment
      * "Opensource vs Comercial vs Construcció a mida”: quan no anem a SaaS o
      serveis administrats en un cloud de referència, en concebre una nova
      solució, s'ha de regir pel següent arbre de decisió:
        * Per a problemes comuns, utilitza "Opensource”.
        * Per a problemes poc comuns, compra.
        * Per a problemes únics, construeix.
      * És molt possible que una solució estigui composada per diferents peces,
      així que l'aplicació d'aquests punt, pot aplicar a una part de la solució
      (per exemple, escollir un producte opensource, però adaptat amb
      desenvolupament a mida) o bé, ens podem trobar que la voluntat
      d'excel·lència i diferenciació de la UOC, ens porti a fer un
      desenvolupament a mida.

      * A l'hora de triar entre utilitzar un producte (opensource o comercial) o
      fer un desenvolupament a mida cal fer una avaluació del cost vs. benefici
      de l'opció triada respecte a les altres.

      * Pensa en l'impacte d'actualització que pugui tenir un canvi de sistema
      operatiu, middleware o producte allà on corre l'aplicació: quant menys
      acoblament amb el sistema de base i utilitzant estàndards, més senzilla
      serà l'actualització o l'ampliació de funcionalitats de l'aplicació.
    titol: Principis sobre el cost i manteniment de les solucions
---
 

