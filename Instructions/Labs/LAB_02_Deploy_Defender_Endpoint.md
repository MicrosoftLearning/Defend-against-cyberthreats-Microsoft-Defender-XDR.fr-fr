---
lab:
  title: Déployer Microsoft Defender pour point de terminaison
  module: Mitigate threats using Microsoft Defender for Endpoint'
---

# Déployer Microsoft Defender pour point de terminaison

## Scénario de labo

Vous êtes analyste des opérations de sécurité dans une entreprise qui implémente Microsoft Defender pour point de terminaison. Votre responsable prévoit d’intégrer quelques appareils afin de fournir des informations sur les modifications requises des procédures de réponse de l’équipe chargée des opérations de sécurité.

La première étape consiste à initialiser l’environnement Defender pour point de terminaison. Dans la suite du labo, vous intégrez les appareils initiaux pour votre déploiement en exécutant le script d’intégration sur les appareils. Vous configurez la sécurité pour l’environnement. Pour terminer, vous créez des groupes d’appareils et vous affectez les appareils appropriés.

>**Important :** les machines virtuelles du labo sont utilisées via différents modules. Assurez-vous d’enregistrer vos machines virtuelles. Si vous quittez le labo sans enregistrer, vous devrez réexécuter certaines configurations.

>**Remarque :** vérifiez que vous avez terminé la tâche 1 du module précédent.

Vous devriez terminer cet exercice en **15** minutes environ.

### Tâche 1 : initialiser Microsoft Defender pour point de terminaison

Dans cette tâche, vous effectuez l’initialisation de Microsoft Defender pour point de terminaison.

1. Connectez-vous à la machine virtuelle **WIN1** en tant qu'administrateur avec le mot de passe suivant : **Pa55w.rd**.  

1. Si vous n’êtes pas déjà sur le portail Microsoft Defender XDR, lancez le navigateur Microsoft Edge.

1. Dans le navigateur Microsoft Edge, accédez au portail Defender XDR à l’adresse (<https://security.microsoft.com>).

1. Dans la boîte de dialogue **Se connecter** , copiez et collez le compte de messagerie du locataire pour le nom d’utilisateur administrateur fourni par votre fournisseur d’hébergement de labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer le mot de passe**, copiez et collez le mot de passe du locataire de l’administrateur fourni par votre fournisseur d’hébergement de labo, puis sélectionnez **Se connecter**.

    >**Conseil :** le compte de messagerie et le mot de passe du locataire de l’administrateur sont disponibles sous l’onglet Ressources.

1. Sur le portail **Defender XDR**, dans le menu de navigation de gauche, faites défiler vers le bas et développez la section **Système**, puis sélectionnez **Paramètres**.

1. Dans la page Paramètres, sélectionnez **Découverte de l’appareil**.

    >**Remarque :**  si l’option **Découverte de l’appareil** n’est pas affichée sous **Paramètres**, déconnectez-vous en sélectionnant le cercle en haut à droite qui indique les initiales de votre compte, puis sélectionnez **Se déconnecter**. Vous pouvez également essayer d’actualiser la page avec Ctrl + F5 ou ouvrir la page en mode InPrivate. Connectez-vous à nouveau avec les informations d’identification de **l’adresse e-mail du locataire**.

1. Dans Configuration de la découverte, assurez-vous que l’option **Découverte standard (recommandée)** est sélectionnée. 

    >**Conseil :** si l’option n’est pas affichée, actualisez la page.


### Tâche 2 : intégrer un appareil

Dans cette tâche, vous allez intégrer un appareil à Microsoft Defender pour point de terminaison à l’aide d’un script d’intégration.

1. Dans le portail **Defender XDR**, dans le menu de navigation à gauche, faites défiler vers le bas, développez la section **Système** et sélectionnez **Paramètres**. Ensuite, depuis la page Paramètres, sélectionnez **Points de terminaison**.

1. Dans la section Gestion des appareils, sélectionnez **Intégration**.

    >**Remarque :** vous pouvez également effectuer l’intégration des appareils à partir de la section **Ressources**, dans la barre de menus de gauche. Développez Ressources et sélectionnez Appareils. Dans la page Inventaire des appareils, avec Ordinateurs et appareils mobiles sélectionné, faites défiler vers le bas jusqu’à **Intégrer des appareils.** Ceci vous dirige vers la page **Paramètres > Points de terminaison**.

1. Dans la zone « 1. Intégrer un appareil », assurez-vous que « Script local (pour jusqu’à 10 appareils) » s’affiche dans la liste déroulante Méthode de déploiement et sélectionnez le bouton **Télécharger le package d’intégration**.

1. Dans la fenêtre contextuelle *Téléchargements*, mettez en surbrillance le fichier « WindowsDefenderATPOnboardingPackage.zip » avec votre souris et sélectionnez l’icône de dossier **Afficher dans le dossier**. **Conseil :** si vous ne voyez pas le fichier, accédez au répertoire c:\users\admin\downloads.

    >**Conseil :** si votre navigateur bloque le téléchargement, prenez des mesures dans le navigateur pour l’autoriser. Dans le navigateur Microsoft Edge, le message suivant « *WindowsDefenderATPOnboardingPackage.zip n’est pas couramment téléchargé. Assurez-vous que vous faites confiance...*, sélectionnez le bouton des points de suspension (...) si nécessaire, puis cliquez sur **Garder**. Dans Microsoft Edge, une deuxième fenêtre contextuelle s’affiche avec le message suivant « * Assurez-vous que vous faites confiance à WindowsDefenderATPOnboardingPackage.zip avant de l’ouvrir* », sélectionnez **Afficher plus** pour développer les sélections et cliquez sur **Garder quand même**.

1. Cliquez avec le bouton droit sur le fichier zip téléchargé et sélectionnez **Extraire tout...**, assurez-vous de cocher la case *Afficher les fichiers extraits une fois l’opération terminée*, puis cliquez sur **Extraire**.

1. Cliquez avec le bouton droit sur le fichier extrait « WindowsDefenderATPLocalOnboardingScript.cmd » et sélectionnez **Propriétés**. Cochez la case **Débloquer** en bas à droite de la fenêtre Propriétés, puis sélectionnez **OK**.

1. Cliquez avec le bouton droit sur le fichier extrait « WindowsDefenderATPLocalOnboardingScript.cmd », puis choisissez **Exécuter en tant qu’administrateur**.  **Conseil :** si la fenêtre Windows SmartScreen, sélectionnez **Plus d’informations**, puis cliquez sur **Exécuter quand même**.

1. Lorsque la fenêtre « Contrôle de compte d’utilisateur » s’affiche, sélectionnez **Oui** pour autoriser l’exécution du script et répondre **Y** à la question présentée par le script, puis appuyez sur **Entrée**. Une fois l’opération terminée, un message doit s’afficher dans l’écran de commande indiquant que *Machine intégrée à Microsoft Defender pour point de terminaison*.

1. Appuyez sur une touche pour continuer. Cette opération ferme la fenêtre d’invite de commandes.

### Tâche 3 : configurer des rôles

Dans cette tâche, vous configurez des rôles et les attribuez à des groupes d’appareils.

1. Dans le menu de navigation du portail Microsoft Defender XDR, développez la section **Système**, sélectionnez **Paramètres**, puis **Microsoft Defender XDR**.

1. Dans la section *Compte*, sélectionnez **Autorisations et rôles**.

1. Faites défiler la page vers le bas et sélectionnez le lien **Accéder aux autorisations et aux rôles**.

1. Sur la page *Autorisations et rôles*, sélectionnez **+ Créer un rôle personnalisé**.

1. Sur la page *Informations de base*, dans la boîte de dialogue Ajouter un rôle, entrez les informations suivantes :

    |Paramètre de base|Valeur|
    |---|---|
    |Nom de rôle|**Support de niveau 1**|

1. Cliquez sur **Suivant**.

1. Sur la page **Autorisations**, sélectionnez les autorisations suivantes :

    |Groupe d’autorisations|Description|  |Opérations de sécurité|Gère les opérations quotidiennes et répond aux incidents et aux avis|

1. Sur la page contextuelle des *Opérations de sécurité*, cochez la case d’option **Toutes les autorisations de lecture et de gestion**.

1. Sélectionnez **Appliquer**, puis **Suivant**.

1. Sur la page **Affecter des utilisateurs et des sources de données**, sélectionnez le bouton **Créer une affectation**.

1. Dans la boîte de dialogue *Ajouter une affectation*, entrez les informations suivantes :

    |Paramètres d’affectation|Valeur|
    |---|---|
    |Nom de l’attribution|**Support de niveau 1**|
    |Employees|****sg-IT**|
    |Sources de données|**Conserver la valeur par défaut**|

1. Sélectionnez **Ajouter**, puis **Suivant**.

1. Sélectionnez **Envoyer**, puis **Terminé** lorsque vous avez terminé.

### Tâche 4 : configurer des groupes d’appareils

Dans cette tâche, vous configurez des groupes d’appareils et spécifiez le contrôle d’accès et l’automatisation.

1. Dans la barre de menus de gauche du portail Microsoft Defender XDR, développez la section **Système**, puis sélectionnez **Paramètres**. Ensuite, sélectionnez **Points de terminaison**.

1. Sous la zone Autorisations, sélectionnez **Groupes d’appareils**.

1. Sélectionnez l’icône **+ Ajouter un groupe d’appareils**.

1. Sous l’onglet Général, entrez les informations suivantes :

    |Paramètres généraux|Valeur|
    |---|---|
    |Nom du groupe d’appareils|**Regular**|
    |Niveau de correction|Correction complète|

1. Cliquez sur **Suivant**.

1. Sous l’onglet Périphériques, pour la condition de système d’exploitation, sélectionnez **Windows 11**, puis **Suivant**.

    >**Note :** certains fournisseurs d’hébergement de labo peuvent avoir configuré des images *Windows 10* pour WIN1. Vous pouvez sélectionner l’un ou l’autre, ou les deux.

1. Sous l’onglet Aperçu des appareils, le bouton *Afficher l’aperçu* peut afficher la machine virtuelle WIN1, mais il est probable que les données ne soient pas encore remplies. Sélectionnez **Suivant** pour continuer.

1. Pour l’onglet Accès utilisateur, sélectionnez **sg-IT**, puis le bouton **Ajouter des groupes sélectionnés**. Vérifiez qu’il apparaît sous *Groupes d’utilisateurs Azure AD ayant accès à ce groupe d’appareils*.

1. Sélectionnez **Envoyer**, puis **Terminé** lorsque vous avez terminé.

1. Sur le message d’information *La configuration du groupe d’appareils a changé. Appliquez les modifications pour vérifier les correspondances et recalculer les regroupements*, sélectionnez **Appliquer les modifications**.

1. Vous aurez maintenant deux groupes d’appareils : le groupe « Normal » que vous venez de créer et le groupe « Appareils non groupés (par défaut) » avec le même niveau de correction.

## Passez à l’exercice 2
