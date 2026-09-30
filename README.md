# Module PrestaShop pour ChatGPT Ads et OpenAI Ads

**Module PrestaShop ChatGPT Ads, pixel OpenAI Ads et suivi des conversions côté serveur**, développé par **Emre Ucak — [Allaux](https://allaux.fr/)**, développeur e-commerce indépendant.

Cette intégration PrestaShop associe le **pixel ChatGPT Ads** et la **Conversions API OpenAI Ads (CAPI)** pour suivre les achats, demandes de devis, ajouts au panier et créations de compte. Elle s'adresse aux boutiques qui souhaitent installer ChatGPT Ads sur PrestaShop et relier leurs événements e-commerce à leur mesure publicitaire.

👉 **[Installation du module PrestaShop ChatGPT Ads et accompagnement technique : contacter Allaux](https://allaux.fr/contact)**

📧 **E-mail : [contact@allaux.fr](mailto:contact@allaux.fr)**  
💬 **WhatsApp : [+33 6 21 86 33 28](https://wa.me/33621863328)**  
🌐 **Site : [allaux.fr](https://allaux.fr/)**

## Suivi des conversions ChatGPT Ads sur PrestaShop

| Parcours | Événement |
|---|---|
| Pages et fiches produits | `page_viewed`, `contents_viewed` |
| Ajout au panier et début de commande | `items_added`, `checkout_started` |
| Demandes de devis et formulaire de contact | `lead_created` |
| Commandes | `order_created` |
| Création de compte | `registration_completed` |
| Connexion réussie et ouverture du devis | Événements personnalisés `login`, `devis_ouvert` |

Les événements peuvent être activés séparément depuis le back-office. Le module comprend une file d'attente, des relances, des logs et un diagnostic téléchargeable. Le tracking navigateur et le tracking serveur utilisent des identifiants partagés pour la déduplication des conversions. La clé API reste côté serveur ; les identifiants clients sont normalisés puis hachés SHA-256.

## Pixel OpenAI Ads et Conversions API PrestaShop

Le pixel mesure les événements dans le navigateur. La Conversions API envoie les événements depuis le serveur de la boutique. Les deux canaux peuvent mesurer la même conversion avec le même identifiant, afin de limiter les doublons dans le suivi publicitaire.

L'intégration prévoit les formats d'événements OpenAI Ads, les montants en unités monétaires mineures, les identifiants d'attribution lorsqu'ils sont disponibles et les erreurs de transmission. Un événement accepté par l'API doit ensuite être vérifié dans la configuration des conversions Ads Manager : acceptation technique et attribution publicitaire sont deux étapes distinctes.

## Consentement, Google Consent Mode et Tarteaucitron

Le suivi nécessite un accord explicite. L'intégration utilise les décisions Google Consent Mode et propose un service Tarteaucitron ainsi que des callbacks pour d'autres gestionnaires de consentement (CMP). Le module bloque les événements avant l'accord et prend en charge le retrait du consentement. La configuration CMP et le thème doivent être vérifiés sur chaque boutique.

## Installation et configuration du module ChatGPT Ads

L'intervention comprend le déploiement du module, la configuration du Pixel ID et de la clé Conversions API, la sélection des événements, la connexion au gestionnaire de consentement et les tests en mode validation. Les formulaires de devis ou modules spécifiques peuvent nécessiter une adaptation pour déclencher la conversion après un envoi réussi.

Pour une boutique existante, l'installation vérifie aussi les pixels déjà présents, les risques de doublons, les caches PrestaShop et la planification des relances.

- [Développeur PrestaShop indépendant](https://allaux.fr/prestashop)
- [Développement de modules PrestaShop sur mesure](https://allaux.fr/prestashop/module-sur-mesure)
- [Intégration de tracking e-commerce, pixels et API](https://allaux.fr/services/tracking)

## Compatibilité et validation

La version 1.1.1 a été vérifiée sous **PrestaShop 8.2.0 / PHP 8.1.34**. Les neuf formats ont été acceptés par OpenAI en mode validation. Les tests dans un navigateur ont couvert pages, produits, ouverture du devis, panier et début de commande ; les hooks de compte ont été testés séparément. Les autres versions PrestaShop, thèmes et modules tiers nécessitent une vérification spécifique. La recette de paiement fait partie de la validation propre à chaque boutique.

Ce dépôt présente les fonctionnalités du module. Pour obtenir le module, le faire installer ou adapter le tracking à votre boutique, [contactez Allaux](https://allaux.fr/contact). Le code et les archives ne sont pas distribués dans ce dépôt public.

## Questions fréquentes : PrestaShop et ChatGPT Ads

### Comment installer le pixel ChatGPT Ads sur PrestaShop ?

L'intégration renseigne le Pixel ID, relie le consentement et déclenche les événements aux étapes pertinentes du parcours client. Il faut aussi vérifier qu'un autre script du thème ne mesure pas déjà les mêmes événements.

### Peut-on suivre les conversions OpenAI Ads côté serveur ?

Oui. Le module utilise la Conversions API OpenAI Ads avec une clé stockée sur le serveur, une file d'attente et des relances en cas d'erreur temporaire.

### Quels événements e-commerce sont pris en charge ?

Le module couvre les pages et produits consultés, ajouts au panier, débuts de commande, achats, demandes de devis, contacts, créations de compte et connexions réussies, selon les déclencheurs disponibles sur la boutique.

### Le module publie-t-il des campagnes publicitaires ?

Il sert au suivi des conversions PrestaShop et à la mesure des événements. La création et la gestion des campagnes s'effectuent dans Ads Manager.

### Qui développe et installe cette intégration PrestaShop ?

Emre Ucak, développeur e-commerce indépendant sous le nom **Allaux**. [Présenter votre projet PrestaShop ou votre besoin de tracking ChatGPT Ads](https://allaux.fr/contact).

## Contacter Allaux pour votre boutique PrestaShop

Pour installer un module ChatGPT Ads, connecter le pixel OpenAI Ads ou mettre en place le suivi des conversions serveur sur PrestaShop :

- **E-mail : [contact@allaux.fr](mailto:contact@allaux.fr)**
- **WhatsApp : [+33 6 21 86 33 28](https://wa.me/33621863328)**
- **Présentation du projet : [allaux.fr/contact](https://allaux.fr/contact)**

## Références techniques

- [Pixel OpenAI Ads](https://developers.openai.com/ads/measurement-pixel)
- [Conversions API](https://developers.openai.com/ads/conversions-api)
- [Événements pris en charge](https://developers.openai.com/ads/supported-events)

Projet indépendant développé par Allaux, sans affiliation ni certification OpenAI ou PrestaShop.
