---
hidden: true
nav_title: CocoaPods
article_title: Intégration de CocoaPods pour iOS
platform: iOS
page_order: 2
description: "Cet article de référence montre comment intégrer le SDK Braze à l’aide de CocoaPods pour iOS."

---

# Intégration de CocoaPods

## Étape 1 : Installer CocoaPods

L’installation du SDK pour iOS via [CocoaPod][apple_initial_setup_1] permet d’automatiser la majorité du processus d’installation pour vous. Avant de lancer ce processus, assurez-vous d’utiliser la [Version Ruby 2.0.0][apple_initial_setup_2] ou ultérieure. Ne vous inquiétez pas, il n’est pas nécessaire que la syntaxe Ruby soit utilisée pour installer ce SDK.

Exécutez la commande suivante pour démarrer :

```bash
$ sudo gem install cocoapods
```

Si vous avez des questions concernant les CocoaPods, consultez le [guide de résolution des problèmes][apple_initial_setup_25] des CocoaPods.

{% alert note %}
Si vous êtes invité à remplacer l’exécutable `rake`, reportez-vous au [Démarrage](http://guides.cocoapods.org/using/getting-started.html "CocoaPods Installation Directions") sur CocoaPods.org pour plus de détails.
{% endalert %}

## Étape 2 : Construction du Podfile

Maintenant que vous avez installé le CocoaPods Ruby Gem, vous devez créer un fichier dans votre répertoire de projet Xcode nommé `Podfile`.

Ajoutez la ligne suivante à votre Podfile :

```
target 'YourAppTarget' do
  pod 'Appboy-iOS-SDK'
end
```

Nous vous suggérons la version Braze afin que les mises à jour du pod récupèrent automatiquement tout ce qui est plus petit qu’une mise à jour mineure de la version. Cela ressemble à `pod 'Appboy-iOS-SDK' ~> Major.Minor.Build`. Si vous souhaitez intégrer automatiquement la dernière version de Braze SDK, même avec des modifications majeures, vous pouvez utiliser `pod 'Appboy-iOS-SDK'` dans votre Podfile.

#### Sous-spécifications

Nous recommandons aux intégrateurs d’importer notre SDK complet. Cependant, si vous êtes certain que vous allez intégrer uniquement une fonction Braze spécifique, vous pouvez importer uniquement la sous-spécification de l’interface utilisateur souhaitée plutôt que le SDK complet.

| Sous-spécifications | Détails |
| ------- | ------- |
| `pod 'Appboy-iOS-SDK/InAppMessage'` | La sous-spécification `InAppMessage` contient l’IU du message in-app de Braze et le SDK Core.|
| `pod 'Appboy-iOS-SDK/ContentCards'` | La sous-spécification `ContentCards` contient l’IU de la carte de contenu de Braze et le SDK Core. |
| `pod 'Appboy-iOS-SDK/NewsFeed'` | La sous-spécification `NewsFeed` contient l’IU du fil d’actualités de Braze et le SDK Core. |
| `pod 'Appboy-iOS-SDK/Core'` | La sous-spécification `Core` contient un support pour l’analytique, comme par exemple, les événements personnalisés et les attributs. |
{: .ws-td-nw-1}

## Étape 3 : Installer le SDK Braze

Pour installer le Braze SDK Cocoapod, accédez au répertoire de votre projet d’application Xcode au sein de votre terminal et exécutez la commande suivante :
```
pod install
```

À ce stade, vous devriez pouvoir ouvrir le nouvel espace de travail du projet Xcode créé par CocoaPods. Assurez-vous d’utiliser cet espace de travail Xcode au lieu de votre projet Xcode. 

![Un dossier Exemple d’Appboy étendu apparaît pour afficher le nouveau `AppbpyExample.workspace`.][apple_initial_setup_15]

## Étapes suivantes

Suivez les instructions pour [compléter l’intégration]({{site.baseurl}}/developer_guide/platform_integration_guides/ios/initial_sdk_setup/completing_integration/).

## Mettre à jour le SDK Braze par CocoaPods

Pour mettre à jour un Cocoapod, il vous suffit de lancer la commande suivante dans votre répertoire de projet :

```
pod update
```

[apple_initial_setup_1]: http://cocoapods.org/
[apple_initial_setup_2]: https://www.ruby-lang.org/en/installation/
[apple_initial_setup_3]: http://guides.cocoapods.org/using/getting-started.html "CocoaPods Installation Directions"
[apple_initial_setup_5]: https://github.com/braze-inc/braze-ios-sdk/blob/master/AppboyKit/include/Appboy.h
[apple_initial_setup_15]: {% image_buster /assets/img_archive/podsworkspace.png %}
[apple_initial_setup_25]: http://guides.cocoapods.org/using/troubleshooting.html "CocoaPods Troubleshooting Guide"
