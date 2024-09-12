.. note::

    Bonjour et bienvenue dans la communauté SunFounder Raspberry Pi & Arduino & ESP32 sur Facebook ! Plongez dans l'univers de Raspberry Pi, Arduino et ESP32 avec d'autres passionnés.

    **Pourquoi nous rejoindre ?**

    - **Support d'experts** : Résolvez les problèmes après-vente et les défis techniques grâce à l'aide de notre communauté et de notre équipe.
    - **Apprendre et partager** : Échangez des astuces et des tutoriels pour perfectionner vos compétences.
    - **Aperçus exclusifs** : Accédez en avant-première aux annonces de nouveaux produits et aux avant-goûts.
    - **Réductions spéciales** : Profitez de réductions exclusives sur nos derniers produits.
    - **Promotions festives et concours** : Participez à des concours et promotions lors des fêtes.

    👉 Prêt à explorer et créer avec nous ? Cliquez [|link_sf_facebook|] et rejoignez-nous dès aujourd'hui !

3. Mesurer avec un multimètre
==========================================

Bienvenue dans notre exploration du multimètre, un outil essentiel en électronique. Cette leçon vous guidera à travers les fonctionnalités et l'utilisation du multimètre, vous apprenant à mesurer efficacement différentes propriétés électriques. En partant des bases, comme l'installation de la batterie et des sondes de test, nous aborderons les réglages et les nombreuses fonctions de l'appareil. Cette expérience pratique vous fournira à la fois des connaissances théoriques et des compétences pour effectuer des mesures précises sur n'importe quel circuit.

Voici ce que vous allez accomplir :

* Comprendre les composants et les fonctions d'un multimètre.
* Maîtriser la mesure de la tension, du courant et de la résistance.
* Améliorer votre compréhension des fondamentaux de l'électronique grâce à la pratique.

Cette leçon renforcera non seulement vos compétences techniques, mais fournira également des connaissances pratiques, posant une base solide pour vos futurs apprentissages et projets en électronique.

En savoir plus sur le multimètre
------------------------------------

Un multimètre est un appareil utilisé pour mesurer différentes propriétés électriques. La plupart des multimètres peuvent mesurer la tension, le courant, la résistance et la continuité (si l'électricité peut circuler).

Le cadran du multimètre vous permet de sélectionner le type de mesure électrique et la plage que vous souhaitez mesurer. Voyons maintenant les différentes fonctions disponibles sur le cadran.

.. image:: img/multimeter_dashboard.png
    :width: 300
    :align: center


**Tension continue (DC)**


Sur cette image, la position sélectionnée sert à mesurer la tension en courant continu (DC). La tension est représentée par un V majuscule. Le DC est symbolisé par trois lignes en pointillés sous une ligne droite.

Votre multimètre dispose de cinq plages différentes de tension continue : 200m (millivolts), 2V (volts), 20V (volts), 200V (volts) et 600V (volts). Ces nombres représentent la tension maximale pouvant être mesurée dans chaque réglage.

.. image:: img/multimeter_dc.png
    :width: 300
    :align: center

.. note::

    Here's the conversion between Volts:

    * 1 millivolt (mV) = 0.001 volt (V)

    Par exemple, si vous avez une tension de 500 millivolts (mV), elle peut également être exprimée sous forme de 0,5 volts (V).


**Méthode de mesure** : Avant de mesurer la tension, vous devez sélectionner une plage de mesure appropriée. Dans tous nos cours, la tension du circuit ne dépassera pas 5V, vous pouvez donc simplement sélectionner la position 20V. Lorsque le circuit fonctionne normalement, vous pouvez tester la tension en plaçant les sondes de test rouge et noire de chaque côté de l'appareil.

**Tension alternative (AC)**

Cette image montre le réglage pour mesurer la tension en courant alternatif (AC). Le courant alternatif est représenté par une ligne ondulée.

.. image:: img/multimeter_ac.png
    :width: 300
    :align: center

**Transistors**

Le réglage hFE NPN PNP est destiné à mesurer les transistors. Vous n'utiliserez pas ce réglage dans ce cours.

.. image:: img/multimeter_hfe.png
    :width: 300
    :align: center

**1.5V mA**

Le réglage "1.5V mA" sur un multimètre est utilisé pour mesurer le courant à un niveau de tension de 1,5V, généralement pour tester la quantité de courant consommée par un circuit ou un appareil à cette tension.

.. image:: img/multimeter_1.5v.png
    :width: 300
    :align: center

**Courant**

Pour mesurer le courant, le multimètre propose des réglages pour 2m (2 milliampères), 20m (20 milliampères), 200m (200 milliampères) et 10A (10 ampères).

.. image:: img/multimeter_current.png
    :width: 300
    :align: center

.. note::

    Voici la conversion entre les ampères :

    * 1 milliampere (mA) = 0.001 ampere (A)

    Par exemple, si vous avez un courant de 50 milliampères (mA), il peut également être exprimé sous forme de 0,05 ampère (A).



Pour mesurer des courants inférieurs à 200 milliampères, vous pouvez insérer la sonde de test rouge dans le port VΩmA. Ensuite, tournez le cadran vers l'un des réglages en milliampères. Les circuits que vous construirez dans ce cours auront toujours des courants inférieurs à 200 mA.

Pour mesurer des courants jusqu'à 10 ampères, vous devez insérer la sonde de test rouge dans le port 10ADC. Ensuite, tournez le cadran sur le réglage 10A.

.. image:: img/multimeter_10a.png
    :width: 300
    :align: center

**Méthode de mesure** : Pour mesurer le courant dans un circuit, le multimètre doit être inséré dans le circuit. Autrement dit, il doit faire partie du circuit. Cela diffère de la mesure de la tension ou de la résistance, qui peut être réalisée à travers un composant dans le circuit. Vous aurez l'occasion de faire ces mesures plus tard, lorsque vous commencerez à construire des circuits.

**Continuité**

Le réglage avec un symbole de diode et une icône sonore est utilisé pour mesurer la continuité. Lors de la mesure de la continuité, si un courant peut circuler entre les sondes de test, le multimètre émet un bip sonore.

.. image:: img/multimeter_diode.png
    :width: 300
    :align: center

**Résistance**

Le dernier ensemble d'options du multimètre est destiné à évaluer la résistance, symbolisée par la lettre grecque oméga (Ω). En général, les multimètres offrent plusieurs plages de mesure pour la résistance. Ce multimètre particulier est équipé de cinq plages : 200 ohms, 2k (2 000 ohms), 20k (20 000 ohms), 200k (200 000 ohms) et 2M (2 000 000 ohms). Chaque plage indique la valeur maximale de résistance qu'il peut mesurer avec précision. Pour obtenir les mesures les plus précises, sélectionnez une plage qui permet de mesurer la résistance sans dépasser la limite supérieure.

.. image:: img/multimeter_resistance.png
    :width: 300
    :align: center
  
.. note::

    Voici la conversion entre les ohms :

    * 1 kilohm (kΩ) = 1000 ohms (Ω)
    * 1 megohm (MΩ) = 1000000 ohms (Ω)

Par exemple, si vous avez une résistance de 1 000 ohms (Ω), cela peut également être exprimé sous forme de 1 kilohm (kΩ).


**Conseils**


Lors de la mesure de la résistance, de la tension ou du courant, vous remarquerez peut-être que les valeurs affichées tendent à varier. Pour stabiliser et capturer une lecture spécifique, vous pouvez utiliser la fonction HOLD. Cette action fige la valeur actuelle sur l'écran, qui y restera jusqu'à ce que vous appuyiez à nouveau sur le bouton HOLD.

Si vous n'êtes pas certain de la plage appropriée à choisir pour mesurer la tension, le courant ou la résistance, il est conseillé de commencer par la plage maximale disponible. Cela vous permet d'obtenir une estimation initiale des valeurs que vous manipulez, puis de réduire ensuite la plage pour des mesures plus précises.

**Question**

Maintenant que vous avez une compréhension détaillée de l'utilisation d'un multimètre, réfléchissez à quel réglage du multimètre vous utiliseriez pour mesurer les valeurs électriques suivantes :

.. list-table::
  :widths: 25 25
  :header-rows: 1

  * - Objet de mesure
    - Réglage du multimètre
  * - 9V DC
    -
  * - 1K ohms
    -
  * - 40 milliamps
    - 
  * - 110V AC
    -


Mesurer avec un multimètre
--------------------------------

Dans la leçon précédente, vous avez monté un circuit simple pour allumer une LED. Maintenant, nous allons utiliser un multimètre pour mesurer la tension, le courant et la résistance dans ce circuit. Voyons comment procéder !

**Préparer le multimètre**

Avant d'utiliser le multimètre, vous devez installer la pile et connecter les deux sondes de test, afin qu'il soit prêt à être utilisé à tout moment.

1. Suivez la vidéo ci-dessous pour connecter la pile à votre multimètre.

  .. raw:: html

      <video width="600" loop autoplay muted>
          <source src="_static/video/3_multimeter_battery.mp4" type="video/mp4">
          Your browser does not support the video tag.
      </video>

2. Trouvez votre multimètre ainsi que les sondes de test rouge et noire. Assurez-vous que le multimètre est en position "off". Insérez la sonde de test noire dans le port COM du multimètre. Insérez la sonde de test rouge dans le port voltage-ohm-milliamp (VΩmA).

.. image:: img/multimeter_test_wire.png
  :width: 300
  :align: center

**Mesurer la tension**

1. Tournez le multimètre sur le réglage 20 volts DC.

.. image:: img/multimeter_dc_20v.png
  :width: 300
  :align: center

2. Écartez légèrement les fils positifs et négatifs sur la plaque d'essai pour exposer les extrémités métalliques sans les détacher complètement.

3. Ensuite, touchez les extrémités métalliques exposées avec les sondes de test rouge et noire du multimètre pour mesurer la tension.

.. image:: img/3_measure_volmeter.png

4. Notez la tension, vous pouvez également enregistrer les phénomènes observés dans la colonne Notes.

.. note::

    * La mienne était de 5,13 volts, remplissez en fonction de votre mesure.

    * En raison de problèmes de câblage et de l'instabilité de votre main, vous pouvez voir la tension fluctuer. Gardez votre main stable, observez plusieurs fois et vous obtiendrez une lecture de tension assez stable.

.. list-table::
   :widths: 25 25 50 25
   :header-rows: 1

   * - Type
     - Unités
     - Résultats de mesure
     - Notes
   * - Tension
     - Volts
     - *≈5,13 volts*
     - 
   * - Courant
     - Milliampères
     - 
     - 
   * - Résistance
     - Ohms
     - 
     -

5. Enfin, réinsérez tous les fils de liaison dans la plaque d'essai pour éviter qu'ils ne soient retirés pendant que vous effectuez d'autres mesures.

**Mesure du courant**

Vous avez mesuré la tension dans le circuit. Maintenant, vous allez mesurer le courant dans le circuit.

1. Pour mesurer le courant, le multimètre doit être intégré dans le chemin de flux du circuit, devenant ainsi une partie du trajet conducteur du circuit. Une méthode simple consiste à ajuster la position de la LED : laissez l'anode de la LED dans le trou 1F tout en déplaçant la cathode (la patte courte) du trou 1E au trou 3E.

.. image:: img/3_measure_current.png
  :width: 600
  :align: center

2. Réglez le multimètre sur la position 200 milliampères.

.. image:: img/multimeter_200ma.png
  :width: 300
  :align: center

3. Placez la sonde de test noire sur le fil connecté au trou 1B et la sonde de test rouge sur la cathode de la LED dans le trou 3E. En complétant cette configuration, la LED rouge devrait commencer à clignoter.

  .. note::

    Lors de la mesure de la tension à travers la résistance et la LED, il peut être difficile d'obtenir une bonne connexion avec les sondes de test du multimètre. Pour améliorer la prise, placez les sondes de test à l'endroit où les pattes des composants entrent dans la breadboard. De cette façon, vous pouvez appuyer plus fort sans déloger les composants.

.. image:: img/3_measure_current2.png

4. Vous constaterez que le courant mesuré est inférieur à 20 mA, nous pouvons donc passer à la position 20 mA pour obtenir une lecture plus précise.

.. image:: img/multimeter_20a.png
  :width: 300
  :align: center

5. Mesurez et enregistrez le courant dans le circuit, en milliampères.

.. note::

  Veuillez noter que des fluctuations du courant mesuré sont normales en raison de divers facteurs tels que la stabilité du contact, les variations de l'alimentation et les effets de température. Nous vous recommandons simplement d'enregistrer la valeur du courant que vous mesurez à un moment donné. Si la valeur est conforme aux attentes théoriques, elle doit être considérée comme acceptable.

  
.. list-table::
   :widths: 25 25 50 25
   :header-rows: 1

   * - Type
     - Unités
     - Résultats de mesure
     - Notes
   * - Tension
     - Volts
     - *≈5.13 volts*
     - 
   * - Courant
     - Milliampères
     - *≈13.54 milliampères*
     - 
   * - Résistance
     - Ohms
     - 
     -

6. Remettez la LED dans sa position d'origine, avec l'anode dans le trou 1F et la cathode dans le trou 1E.

**Calcul de la résistance totale**

Mesurer la résistance dans un circuit à l'aide d'un multimètre devient délicat lorsque des LED sont impliquées, car les LED nécessitent une tension spécifique pour s'allumer, appelée tension de seuil. Si la tension n'est pas suffisante, la LED ne s'allume pas et le circuit reste ouvert, ce qui complique la mesure de la résistance. De plus, il ne doit y avoir aucune autre tension dans le circuit à part celle provenant du multimètre lorsque vous mesurez la résistance.

Donc, mesurer directement la résistance du circuit avec un multimètre n'est pas simple. Que faire alors ?

Ici, nous allons utiliser la formule ci-dessous pour calculer la résistance à partir de la tension et du courant, qui est la loi d'Ohm. Nous vous fournirons une introduction détaillée à ce sujet dans la prochaine leçon.

.. code-block::

    Voltage = Current x Resistance

    Or

    V = I • R

En réarrangeant l'équation, cela devient :

.. code-block::

    Resistance = Voltage / Current

    Or

    R = V / I

En utilisant la formule ci-dessus, avec la tension et le courant que vous avez mesurés, vous pouvez calculer la résistance totale dans le circuit et la renseigner dans le tableau.

.. note::

    La tension est exprimée en volts, la résistance en ohms et le courant dans le tableau est en milliampères, vous devez donc convertir les milliampères en ampères :

    1 Amps = 1000 Milliamps

    Cela signifie que vous devez diviser le courant mesuré par 1000 avant d'utiliser la formule pour calculer la résistance totale. Le résultat final peut ne pas être un nombre entier, veuillez arrondir à deux décimales. Par exemple, ma valeur calculée est de 378,8774002954, que j'arrondis à 378,88.

    R = 5.13 / (13.54 / 1000) = 378.88 ohms


.. list-table::
   :widths: 25 25 50 25
   :header-rows: 1

   * - Type
     - Unités
     - Résultats de mesure
     - Notes
   * - Tension
     - Volts
     - *≈5.13 volts*
     - 
   * - Courant
     - Milliampères
     - *≈13.54 milliampères*
     - 
   * - Résistance
     - Ohms
     - *≈378.88 ohms*
     -

**Mesure de la valeur de résistance**

Maintenant que nous avons calculé la résistance totale du circuit, il est temps de voir quelle part est due à la résistance et quelle part est attribuable à la LED. Notre résistance est marquée comme étant de 220 ohms, mais avec une tolérance de 5 %, elle pourrait en réalité se situer entre 209 et 231 ohms. Utilisons le multimètre pour connaître sa valeur exacte.

1. Lorsque vous mesurez la résistance, votre multimètre doit être la seule source de tension ; assurez-vous qu'il n'y a pas d'autres sources d'alimentation connectées au circuit. Débranchez donc tous les fils de connexion de l'Arduino Uno R3 pour isoler la breadboard.

.. image:: img/3_measure_resistance.png
  :width: 600
  :align: center

2. Pour une mesure précise de la résistance, réglez votre multimètre sur la position 2K (2000 ohms) de la fonction résistance.

.. image:: img/multimeter_2k.png
  :width: 300
  :align: center

3. Placez les sondes de test rouge et noire du multimètre de chaque côté de la résistance, puis notez la valeur affichée.

.. image:: img/3_measure_resistor.png

4. Après avoir effectué la mesure, n'oubliez pas d'éteindre le multimètre en le réglant sur la position "OFF".

**Calcul de la résistance de la LED**

Pour déterminer la résistance de la LED, soustrayez la résistance de la résistance de la résistance totale du circuit.

.. code-block::

    Résistance LED = Résistance totale - Résistance de la résistance

Ainsi, selon mes mesures, la résistance de la LED devrait être : 378,88 - 215 = 163,88 ohms.

Nous avons parcouru ensemble les bases pratiques de l'utilisation d'un multimètre pour mesurer la tension, le courant et la résistance dans un circuit. De la construction d'un simple circuit de LED à l'exploration des subtilités de la mesure de la résistance dans des circuits avec des LED, nous avons appliqué la loi d'Ohm et compris les dynamiques des circuits en série et en parallèle. À mesure que nous avançons, souvenez-vous que ces compétences fondamentales constituent le socle de projets plus complexes et d'une compréhension approfondie de l'électronique. Continuez à expérimenter, à apprendre, et ensemble, continuons à éclairer le chemin de l'exploration électronique.
