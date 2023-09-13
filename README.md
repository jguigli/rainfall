# rainfall

Lorsqu'on se connecte au level0 en ssh avec le mot de passe 'level0' :

	ssh level0@192.168.56.109 -p 4242

On obtient cette sortie :

	GCC stack protector support:            Enabled
	Strict user copy checks:                Disabled
	Restrict /dev/mem access:               Enabled
	Restrict /dev/kmem access:              Enabled
	grsecurity / PaX: No GRKERNSEC
	Kernel Heap Hardening: No KERNHEAP
	System-wide ASLR (kernel.randomize_va_space): Off (Setting: 0)

	RELRO           STACK CANARY      NX            PIE             RPATH      RUNPATH      FILE
	No RELRO        No canary found   NX enabled    No PIE          No RPATH   No RUNPATH   /home/user/level0/level0


GCC stack protector support: 
Cela indique si le support du mécanisme de protection de la pile est activé dans le compilateur GCC (GNU Compiler Collection). Le support du stack protector est activé.

Strict user copy checks: 
Cela indique si des vérifications strictes sont effectuées lors de la copie de données entre l'espace utilisateur et l'espace noyau. Dans votre cas, cette fonctionnalité est désactivée, ce qui signifie que certaines vérifications moins strictes sont utilisées.

Restrict /dev/mem access: 
Cela indique si l'accès au périphérique /dev/mem est restreint. Dans votre cas, cet accès est restreint, ce qui est une mesure de sécurité.

Restrict /dev/kmem access: 
De manière similaire à /dev/mem, cela indique si l'accès au périphérique /dev/kmem est restreint. Dans votre cas, cet accès est également restreint, ce qui est une bonne pratique de sécurité.

grsecurity / PaX: 
Cela indique si votre système exécute les fonctionnalités de sécurité grsecurity et PaX. Dans votre cas, ces fonctionnalités ne semblent pas être activées.

Kernel Heap Hardening: 
Indique si des mécanismes de renforcement de la sécurité sont activés pour le tas du noyau. Dans votre cas, ces mécanismes ne semblent pas être activés.

System-wide ASLR (kernel.randomize_va_space): 
Cela concerne la configuration de l'espacement aléatoire des adresses de mémoire (ASLR) au niveau du système. Dans votre cas, il est désactivé (Setting: 0), ce qui signifie que les adresses de mémoire ne sont pas aléatoirement réorganisées, ce qui peut être considéré comme une mesure de sécurité plus faible.

RELRO, STACK CANARY, NX, PIE, RPATH, RUNPATH: 
Ce sont des caractéristiques de sécurité relatives à l'exécution de programmes et aux bibliothèques. Elles indiquent si certaines protections de sécurité sont activées ou désactivées pour l'exécution du fichier /home/user/level0/level0. Par exemple, l'absence de "RELRO" signifie qu'il n'y a pas de "Relocation Read-Only" (lecture seule de relocalisation) pour ce fichier.


-rwsr-x---+ 1 level1 users 747441 Mar  6  2016 level0

Le caractère '+' à la fin de la ligne dans la sortie des permissions indique la présence d'attributs étendus associés à ce fichier. Les attributs étendus sont des métadonnées supplémentaires que vous pouvez attacher à un fichier pour stocker des informations supplémentaires qui ne sont pas gérées par les permissions traditionnelles de lecture, d'écriture et d'exécution.

Lien format string printf :

https://julianor.tripod.com/bc/formatstring-1.2.pdf
https://repo.zenk-security.com/Techniques%20d.attaques%20%20.%20%20Failles/Les%20failles%20Format%20String.pdf
https://axcheron.github.io/exploit-101-format-strings/