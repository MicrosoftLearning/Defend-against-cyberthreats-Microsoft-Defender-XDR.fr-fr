---
lab:
  title: "Configurer Microsoft\_Defender"
  module: Configure the Microsoft Defender XDR environment
---
Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise qui implémente Microsoft Defender XDR. Votre rôle consiste à aider l’équipe informatique de l’entreprise à se défendre contre les cybermenaces avec Microsoft Defender (XDR). La direction de l’entreprise attache beaucoup d’importance à l’application de toutes les recommandations et au respect de toutes les exigences lors de l’exécution des activités dans son environnement.

# Configurer l’environnement Microsoft Defender XDR

Dans cet exercice, vous allez approvisionner votre environnement Microsoft Defender XDR, intégrer des stations de travail clientes dans Defender pour point de terminaison et effectuer un scénario de simulation d’attaque sur une station de travail cliente.

Vous devriez terminer cet exercice en **10 à 15** minutes environ.

>**Important :** vous devez avoir accès à un locataire Microsoft 365 E5 avec une licence Microsoft Defender for Endpoint P2 pour effectuer les exercices suivants. Vous devez également disposer de stations de travail clientes Microsoft Windows 10 ou 11 pour intégrer et exécuter des attaques simulées.

## Tâche 1 : préparer l’espace de travail Microsoft Defender XDR

1. Dans le navigateur Microsoft Edge, accédez au portail Microsoft Defender à l’adresse (<https://security.microsoft.com>).
1. Dans le portail **Microsoft Defender**, dans le menu de navigation, sélectionnez **Accueil** à gauche.

    >**Remarque :** vous devrez peut-être faire défiler jusque tout en haut du menu.

1. Faites défiler les éléments de menu vers **Ressources** et sélectionnez **Appareils**.

1. Le processus de déploiement de l’espace de travail Defender XDR doit commencer et vous devez voir les messages indiquant *le chargement et l’initialisation* brièvement affichés en haut de la page, puis vous verrez une image d’une tasse de café et un message qui lit : **Tenez bon ! Nous préparons de nouveaux espaces pour vos données et nous les connectons.** La procédure prend environ 5 minutes. *Laissez la page ouverte et assurez-vous que la procédure se termine, car elle est requise pour le labo suivant.*

    >**Remarque :** Ignorez les messages d’erreur contextuels indiquant que *certaines de vos données ne peuvent pas être récupérées*. Si le message « Tenez bon ! Nous préparons de nouveaux espaces pour vos données et nous les connectons » ne s’affiche pas, ou si la page « Paramètres > Microsoft Defender XDR > Compte » s’ouvre, mais que vous voyez le message *Échec du chargement de l’emplacement de stockage des données. Réessayez ultérieurement*, sélectionnez « Paramètres du service d’alerte » dans le menu « Général ».

1. Une fois l’initialisation de l’espace de travail terminée, la page du portail **Accueil** affiche une bannière **Obtenir votre SIEM et XDR en un seul endroit**. Dans **Paramètres**, les paramètres généraux de Microsoft Defender XDR pour le compte, les notifications par e-mail, les **fonctionnalités en préversion**, les paramètres du service d’alerte, les autorisations et les rôles, ainsi que l’API de diffusion en continu sont désormais activés.

### tâche 2 : appliquer des stratégies de sécurité prédéfinies pour Microsoft Defender pour Office 365.

Dans cette tâche, vous allez attribuer des stratégies de sécurité prédéfinies pour Exchange Online Protection (EOP) et Microsoft Defender for Office 365 dans le portail de sécurité Microsoft 365.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur ou Administratrice avec le mot de passe : **Pa55w.rd**.  

1. Ouvrez le navigateur Microsoft Edge.

1. Dans le navigateur Microsoft Edge, accédez au portail Microsoft Defender XDR à l’adresse (<https://security.microsoft.com>).

1. Dans la boîte de dialogue **Se connecter** , copiez et collez le compte de messagerie du locataire pour le nom d’utilisateur administrateur fourni par votre fournisseur d’hébergement de labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer le mot de passe**, copiez et collez le mot de passe du locataire de l’administrateur fourni par votre fournisseur d’hébergement de labo, puis sélectionnez **Se connecter**.

    >**Remarque :** si le message suivant s’affiche « Impossible d’effectuer l’opération. Veuillez réessayer plus tard. Si le problème persiste, contactez le support technique Microsoft ». cliquez sur **OK** pour continuer.  

1. Si elle s’affiche, fermez la fenêtre contextuelle de visite guidée rapide de Microsoft Defender XDR. **Conseil :** Plus loin dans ce labo, vous devez attendre que l’espace de travail Defender soit approvisionné. Vous pouvez profiter de ce moment pour parcourir les visites guidées pour en savoir plus sur Microsoft Defender XDR.

1. Dans le menu de navigation, dans la zone *E-mail et collaboration*, sélectionnez **Stratégies et règles**.

1. Dans le tableau de bord *Stratégie et règles*, sélectionnez **Stratégies contre les menaces**.

1. Dans le tableau de bord *Stratégies contre les menaces*, sélectionnez **Stratégies de sécurité prédéfinies**.

    >**Remarque :** si vous recevez le message *« Erreur du client - Erreur lors de l’obtention de la règle bip »*, sélectionnez **OK** pour continuer. L’erreur est due à l’état d’hydratation de votre locataire sur Office 365, qui n’est pas activé par défaut.

    >**Remarque :** si vous recevez le message *« Erreur du client - Une erreur s’est produite lors de la récupération des stratégies de sécurité prédéfinies. Réessayez plus tard »* sélectionnez **OK** pour continuer. Actualisez votre navigateur à l’aide du raccourci clavier **Ctrl + F5**.

1. Dans la page *contextuelle* **Découvrez les stratégies de sécurité prédéfinies**, sélectionnez **Fermer**.

1. Sous *Protection standard*, sélectionnez **Gérer les paramètres de protection**. **Conseil :** si cette option est grisée, actualisez votre navigateur à l’aide de **Ctrl + F5**.

1. Dans la section *Appliquer Exchange Online Protection*, sélectionnez **Destinataires spécifiques** et sous **Domaines**, commencez à écrire le nom de domaine de votre locataire, sélectionnez-le, puis cliquez sur **Suivant**.

    >**Conseil :** Le nom de domaine de votre locataire est identique à celui de votre compte d’administrateur. Il peut s’agir d’un nom similaire à *WWLx######.onmicrosoft.com*. Notez que cette configuration applique des stratégies anti-courrier indésirable, de filtrage du courrier indésirable sortant, anti-programme malveillant et anti-hameçonnage.

1. Dans la section *Appliquer la protection Defender pour Office 365*, effectuez la même configuration que l’étape précédente et sélectionnez **Suivant**. Notez que cette configuration applique des stratégies anti-hameçonnage, de pièces jointes fiables et de liens fiables.

1. Dans la section *Protection de l’emprunt d’identité*, sélectionnez **Suivant** quatre fois (4x) pour continuer.

1. Dans la section *Mode de stratégie*, vérifiez que la case d’option **Activer la stratégie une fois terminé** est sélectionnée, puis cliquez sur **Suivant**.

1. Lisez le contenu sous *Examinez et confirmez vos modifications* et sélectionnez **Confirmer** pour appliquer les modifications, puis cliquez sur **Terminé**.

    >**Remarque :** si vous recevez le message suivant *« L’URI <https://outlook.office365.com/psws/service.svc/AntiPhishPolicy> n’est pas valide pour l’opération PUT. L’URI doit pointer vers une seule ressource pour les opérations PUT. »* sélectionnez **OK**, puis **annuler** pour revenir à la page principale. Vous verrez que la *Protection standard est activée*.

1. Sous *Protection stricte*, sélectionnez **Gérer les paramètres de protection**. **Conseil :***la protection stricte* se trouve sous « E-mail & Collaboration - Stratégies et règles - Stratégies contre les menaces - Stratégies de sécurité prédéfinies ».

1. Dans *Appliquer Exchange Online Protection*, sélectionnez **Destinataires spécifiques** et sous **Groupes**, commencez à écrire **Leadership**, sélectionnez-le, puis cliquez sur **Suivant**. Notez que cette configuration applique des stratégies anti-courrier indésirable, de filtrage du courrier indésirable sortant, anti-programme malveillant et anti-hameçonnage.

1. Dans la section *Appliquer la protection Defender pour Office 365*, effectuez la même configuration que l’étape précédente et sélectionnez **Suivant**. Notez que cette configuration applique des stratégies anti-hameçonnage, de pièces jointes fiables et de liens fiables.

1. Dans la section *Protection de l’emprunt d’identité*, sélectionnez **Suivant** quatre fois (4x) pour continuer.

1. Dans la section *Mode de stratégie*, vérifiez que la case d’option **Activer la stratégie une fois terminé** est sélectionnée, puis cliquez sur **Suivant**.

1. Lisez le contenu sous *Examinez et confirmez vos modifications* et sélectionnez **Confirmer** pour appliquer les modifications, puis cliquez sur **Terminé**.

    >**Remarque :** si vous recevez le message suivant *« L’URI <https://outlook.office365.com/psws/service.svc/AntiPhishPolicy> n’est pas valide pour l’opération PUT. L’URI doit pointer vers une seule ressource pour les opérations PUT. »* sélectionnez **OK**, puis **annuler** pour revenir à la page principale. Vous verrez que la *Protection stricte est activée*.

## Vous avez terminé le labo
