# .htaccess

Ce projet contient un fichier `.htaccess` qui permet de rediriger les requêtes vers les fichiers `.php` et `.html` de manière transparente. Cela signifie que les utilisateurs peuvent accéder aux pages sans spécifier explicitement l'extension du fichier dans l'URL.

## Contenu du fichier .htaccess

RewriteEngine on

RewriteCond %{REQUEST_FILENAME}.php -f
RewriteRule ^(.*)$ $1.php [NC,L]

RewriteCond %{THE_REQUEST} /([^.]+).php [NC]
RewriteRule ^ /%1 [NC,L,R]

RewriteCond %{REQUEST_FILENAME}.html -f
RewriteRule ^(.*)$ $1.html [NC,L]

RewriteCond %{THE_REQUEST} /([^.]+).html [NC]
RewriteRule ^ /%1 [NC,L,R]


### Explications des règles de réécriture

1. **Activation du moteur de réécriture**

    ```
    RewriteEngine on
    ```

    Cette directive active le moteur de réécriture d'URL.

2. **Redirection des fichiers .php**

    ```
    RewriteCond %{REQUEST_FILENAME}.php -f
    RewriteRule ^(.*)$ $1.php [NC,L]
    ```

    - `RewriteCond %{REQUEST_FILENAME}.php -f` : Vérifie si un fichier avec l'extension `.php` existe.
    - `RewriteRule ^(.*)$ $1.php [NC,L]` : Si la condition précédente est vraie, cette règle réécrit l'URL pour inclure l'extension `.php`.

    ```
    RewriteCond %{THE_REQUEST} /([^.]+)\.php [NC]
    RewriteRule ^ /%1 [NC,L,R]
    ```

    - `RewriteCond %{THE_REQUEST} /([^.]+)\.php [NC]` : Vérifie si la requête d'origine contient `.php`.
    - `RewriteRule ^ /%1 [NC,L,R]` : Redirige la requête vers l'URL sans l'extension `.php`, indiquant au navigateur de changer l'URL visible.

3. **Redirection des fichiers .html**

    ```
    RewriteCond %{REQUEST_FILENAME}.html -f
    RewriteRule ^(.*)$ $1.html [NC,L]
    ```

    - `RewriteCond %{REQUEST_FILENAME}.html -f` : Vérifie si un fichier avec l'extension `.html` existe.
    - `RewriteRule ^(.*)$ $1.html [NC,L]` : Si la condition précédente est vraie, cette règle réécrit l'URL pour inclure l'extension `.html`.

    ```
    RewriteCond %{THE_REQUEST} /([^.]+)\.html [NC]
    RewriteRule ^ /%1 [NC,L,R]
    ```

    - `RewriteCond %{THE_REQUEST} /([^.]+)\.html [NC]` : Vérifie si la requête d'origine contient `.html`.
    - `RewriteRule ^ /%1 [NC,L,R]` : Redirige la requête vers l'URL sans l'extension `.html`, indiquant au navigateur de changer l'URL visible.

## Utilisation

1. **Placer le fichier .htaccess**

    Placez ce fichier `.htaccess` à la racine de votre projet ou dans le répertoire où vous souhaitez appliquer ces règles de réécriture.

2. **Vérifier les redirections**

    Accédez à vos pages sans spécifier les extensions `.php` ou `.html` dans l'URL. Par exemple, au lieu d'accéder à `http://votre-domaine.com/page.php`, vous pouvez simplement utiliser `http://votre-domaine.com/page`.

## Conclusion

Avec ce fichier `.htaccess`, vous pouvez rendre vos URL plus propres et plus faciles à mémoriser en supprimant les extensions de fichier visibles. Cela améliore l'expérience utilisateur et peut également bénéficier au référencement de votre site.
