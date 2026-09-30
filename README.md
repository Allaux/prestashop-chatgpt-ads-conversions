# Module PrestaShop pour ChatGPT Ads et OpenAI Ads

**Module PrestaShop ChatGPT Ads, pixel OpenAI Ads et suivi des conversions côté serveur**, développé par **Emre Ucak — [Allaux](https://allaux.fr/)**, développeur e-commerce indépendant.

Cette intégration PrestaShop associe le **pixel ChatGPT Ads** et la **Conversions API OpenAI Ads (CAPI)** pour suivre les achats, demandes de devis, ajouts au panier et créations de compte. Elle s'adresse aux boutiques qui souhaitent installer ChatGPT Ads sur PrestaShop et relier leurs événements e-commerce à leur mesure publicitaire.

Découvrez la [présentation du module ChatGPT Ads pour PrestaShop](https://allaux.fr/prestashop/module-chatgpt-ads) et le [guide du suivi des conversions ChatGPT Ads : pixel OpenAI, Conversions API et consentement](https://allaux.fr/services/tracking/suivi-conversions-chatgpt-ads).

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

Cette mise en place relève d'une [intégration API e-commerce avec gestion de l'authentification et des erreurs](https://allaux.fr/services/integrations-api).

### Attribution publicitaire : oppref, obref et déduplication

Le suivi des ventes issues des annonces ChatGPT utilise notamment **`oppref`**, l'identifiant de clic, et **`obref`**, l'identifiant du navigateur, lorsqu'ils sont disponibles et autorisés par le consentement. Leur transmission complète le rapprochement des conversions ; une réponse API positive ne suffit pas à prouver qu'une vente a été attribuée à une annonce.

La déduplication repose sur un **Pixel ID**, un nom d'événement et un identifiant partagés : `event_id` pour le pixel, `id` pour la Conversions API. Le contrôle porte aussi sur le montant, la devise et le moment réel de l'événement. Le mode **`validate_only`** permet de vérifier les envois serveur sans enregistrer de conversions de test.

### Audit du tracking ChatGPT Ads et conversions manquantes

Un audit vérifie les événements du tunnel de commande, l'ajout au panier AJAX, les pixels présents dans le thème, le cache, le consentement et les envois serveur. Il aide à repérer les achats comptés deux fois, les paramètres d'attribution absents ou les événements qui ne remontent plus après une modification du thème. Allaux décrit cette démarche dans le [diagnostic des conversions qui ne remontent pas](https://allaux.fr/services/tracking/conversions-ne-remontent-pas).

## Consentement, Google Consent Mode et Tarteaucitron

Le suivi nécessite un accord explicite. L'intégration utilise les décisions Google Consent Mode et propose un service Tarteaucitron ainsi que des callbacks pour d'autres gestionnaires de consentement (CMP). Le module bloque les événements avant l'accord et prend en charge le retrait du consentement. La configuration CMP et le thème doivent être vérifiés sur chaque boutique.

Les signaux **`ad_storage`** et **`ad_user_data`** font partie des contrôles de l'intégration. Une bannière Axeptio, Cookiebot, Didomi, CookieYes ou Complianz demande un branchement et une recette adaptés à sa configuration. Le [guide Allaux du mode consentement Google en Europe](https://allaux.fr/services/tracking/mode-consentement-europe) explique les signaux à vérifier ; ce mécanisme ne remplace pas le choix du visiteur.

## Installation et configuration du module ChatGPT Ads

L'intervention comprend le déploiement du module, la configuration du Pixel ID et de la clé Conversions API, la sélection des événements, la connexion au gestionnaire de consentement et les tests en mode validation. Les formulaires de devis ou modules spécifiques peuvent nécessiter une adaptation pour déclencher la conversion après un envoi réussi.

Pour une boutique existante, l'installation vérifie aussi les pixels déjà présents, les risques de doublons, les caches PrestaShop et la planification des relances.

Le suivi doit cohabiter avec le thème et les autres modules sans dégrader le parcours d'achat. Les adaptations peuvent s'inscrire dans une prestation de [développement e-commerce sur mesure](https://allaux.fr/services/developpement-sur-mesure), puis de [maintenance technique PrestaShop](https://allaux.fr/services/maintenance). Les contrôles de chargement et de cache rejoignent les interventions de [performance web et SEO technique e-commerce](https://allaux.fr/services/performance-web).

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

## Articles Allaux sur ChatGPT, PrestaShop et le suivi e-commerce

| Ressource | Sujet |
|---|---|
| [Module ChatGPT Ads pour PrestaShop](https://allaux.fr/prestashop/module-chatgpt-ads) | Installation, conversions, panier et CAPI |
| [Suivi des conversions ChatGPT Ads](https://allaux.fr/services/tracking/suivi-conversions-chatgpt-ads) | Pixel OpenAI, attribution, déduplication et consentement |
| [Conversions qui ne remontent pas](https://allaux.fr/services/tracking/conversions-ne-remontent-pas) | Diagnostic des balises et du parcours d'achat |
| [Mode consentement Google en Europe](https://allaux.fr/services/tracking/mode-consentement-europe) | Signaux de consentement et configuration de la bannière |
| [Extension ChatGPT Ads pour WooCommerce](https://allaux.fr/wordpress-woocommerce/extension-chatgpt-ads) | Autre intégration Allaux pour les boutiques WordPress |
| [PrestaShop MCP : connecter une boutique à un assistant IA](https://allaux.fr/prestashop/mcp) | Accès aux données et outils de la boutique depuis un assistant compatible |
| [Serveur MCP pour boutique pilotable par IA](https://allaux.fr/expertises/serveur-mcp-boutique-pilotable) | Périmètre des outils, droits et traçabilité |

Les articles MCP présentent une prestation distincte du suivi publicitaire : connecter PrestaShop à ChatGPT ou à un autre assistant pour interroger la boutique relève d'un serveur MCP, tandis que ce module mesure les conversions ChatGPT Ads.

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
