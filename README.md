
👋 Hello, I’m @fanzinedebreizh
🔭 I’m currently working on my red thread project !!
🌱 I’m currently learning php and some other stuff at the afpa in Créteil.

2022-04-23 | Création du projet sous Symfony 5-4
================================================
Après moulte essais et deux bugs qui m'ont conduit à devoir désinstaller et à réinstaller XAMPP
j'ai décidé (car j'avais déjà eu des soucis avec MAMP) d'installer WAMP. En effet, le peu que
j'ai pu en voir m'a permis de constater qu'il était plus "paramétrable" que les deux autres.

J'ai installé WAMP version : 
1) Wampserver 3.2.6 64 bit x64 - Apache 2.4.51 - PHP 5.6.40/7.4.26/8.0.13/8.1.0 - MySQL 5.7.36|8.0.27 - MariaDB 10.5.13|10.6.5
Il est indiqué que la va version de PHPMyAdmin contenue dans ce package doit être mise à jour à cause de certaines vulnérabilités
J'ai donc mis à jour en téléchargeant :
2) Wampserver update 3.2.8
3) Phpmyadmin 5.1.3

J'ai paramétré MariaDB pour que cette base de données prime sur MySQL. En effet, dans les essais auxquels j'ai procédé plus haut
les exportations que j'avais effectué avec MariaDB sur XAMPP ne pouvaient être importées dans MySQL sur WAMP. J'ai donc fait ce
choix là. Après quelques réglages, cela fontionne.

Pour créer ce projet :
- Dans une première console se positionner dans le dossier 'www' de WAMP
- Installer un nouveau projet SYMFONY en indiquant le dossier de destination :
	> symfony new rec01-fanzine-de-breizh --version=5.4 --webapp
- Se positionner maintenant dans le répertoire nouvellement créé et installer les bundles :
    > composer install (rien à installer pour l'instant, tout est Ok.)
- Vérifier le .env pour :
    - Les paramètres de connexion à la BD
    > DATABASE_URL="mysql://root:@127.0.0.1:3306/fanzine_de_breizh?serverVersion=10.6.5-MariaDB&charset=utf8mb4"
- Dans une console, j'ai lancé le serveur web :
    > symfony server:start






- Dans une première console, faire le clone
- Installer les bundles :
    > composer install
- Suite à l'installation de CKEditor : 
    > composer update
- Vérifier le .env pour 
    - Les paramètres de connexion à la BD
    - Les paramètres SMTP :
        - Pour SMTP local styme Maildev ou Mailhog :
            > MAILER_DSN=smtp://localhost:1025
            - Puis lancer le service dans une console séparée
            - Et un onglet sur la boite de réception
        - Pour SMTP cloud style Mailtrap :
            > MAILER_DSN=smtp://login:password@smtp.mailtrap.io:2525?encryption=tls&auth_mode=login
            - Puis ouvrir un onglet sur la boite de réception du service
- Créer la BD : 
    > php bin/console doctrine:database:create
- Exécuter les migrations :
    > php bin/console doctrine:migrations:migrate
- Dans une autre console, lancer le serveur web :
    > symfony server:start
- Dans une autre console, lancer le gestionaire de messages :
    > php bin/console messenger:consume async -vv

Cela devrait fonctionner ;-)
