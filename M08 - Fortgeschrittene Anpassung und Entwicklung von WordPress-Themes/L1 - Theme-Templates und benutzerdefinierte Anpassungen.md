
# Theme-Templates und benutzerdefinierte Anpassungen

## Anpassung von Theme-Dateien und Templates für individuelle Layouts

Themes bieten eine Grundlage für das Erscheinungsbild und die Struktur einer Website. Durch die Anpassung von Theme-Dateien und Templates können individuelle Layouts und Designs umgesetzt werden.

### 1. Lokalisieren der Theme-Dateien
- Theme-Dateien befinden sich in der Regel im Ordner `/wp-content/themes/dein-theme/`.
- Wichtige Dateien für Layout-Anpassungen sind:
  - `header.php` (Kopfbereich der Seite)
  - `footer.php` (Fußbereich der Seite)
  - `page.php` und `single.php` (Layout für Seiten und Beiträge)

### 2. Beispiel für die Anpassung des Headers
Öffnen Sie die Datei `header.php` und fügen Sie benutzerdefinierte Elemente hinzu:
```php
<!DOCTYPE html>
<html <?php language_attributes(); ?>>
<head>
    <meta charset="<?php bloginfo( 'charset' ); ?>">
    <title><?php wp_title(); ?></title>
    <?php wp_head(); ?>
</head>
<body <?php body_class(); ?>>
    <header>
        <div class="custom-header">
            <h1>Meine benutzerdefinierte Website</h1>
        </div>
    </header>
```

## Integration benutzerdefinierter Stylesheets und Skripte

Zusätzlich zu den Anpassungen an den Theme-Dateien können benutzerdefinierte CSS- und JavaScript-Dateien integriert werden, um das Erscheinungsbild und die Funktionalität weiter zu erweitern.

### 1. Hinzufügen eines benutzerdefinierten Stylesheets
- Erstellen Sie eine Datei `custom-style.css` im Verzeichnis des Themes.
- Fügen Sie die Datei in die `functions.php` des Themes ein:
```php
function custom_theme_styles() {
    wp_enqueue_style('custom-style', get_template_directory_uri() . '/custom-style.css');
}
add_action('wp_enqueue_scripts', 'custom_theme_styles');
```

### 2. Hinzufügen eines benutzerdefinierten Skripts
- Erstellen Sie eine Datei `custom-script.js` im Verzeichnis des Themes.
- Fügen Sie das Skript ebenfalls in die `functions.php` ein:
```php
function custom_theme_scripts() {
    wp_enqueue_script('custom-script', get_template_directory_uri() . '/custom-script.js', array('jquery'), null, true);
}
add_action('wp_enqueue_scripts', 'custom_theme_scripts');
```

## Verwendung von Child-Themes für nachhaltige Anpassungen

Um sicherzustellen, dass Ihre Anpassungen auch nach Theme-Updates erhalten bleiben, empfiehlt es sich, ein Child-Theme zu erstellen. Ein Child-Theme erbt die Funktionen und das Design des übergeordneten Themes und ermöglicht es Ihnen, nur die spezifischen Dateien und Stile zu ändern, die angepasst werden müssen.

### 1. Erstellen eines Child-Themes
- Erstellen Sie einen neuen Ordner im Verzeichnis `/wp-content/themes/` mit dem Namen des Child-Themes, z.B. `mein-child-theme`.
- Erstellen Sie eine `style.css` Datei im neuen Ordner mit folgendem Inhalt:
```css
/*
 Theme Name: Mein Child Theme
 Template: übergeordnetes-theme
*/
```

- Erstellen Sie eine `functions.php` Datei im Child-Theme und fügen Sie folgenden Code hinzu, um die Styles des übergeordneten Themes zu laden:
```php
function my_child_theme_enqueue_styles() {
    wp_enqueue_style('parent-style', get_template_directory_uri() . '/style.css');
}
add_action('wp_enqueue_scripts', 'my_child_theme_enqueue_styles');
```

### 2. Anpassen von Dateien im Child-Theme
- Kopieren Sie die Datei, die Sie anpassen möchten (z.B. `header.php`), aus dem übergeordneten Theme in das Child-Theme.
- Nehmen Sie die gewünschten Änderungen an der kopierten Datei vor. Diese Änderungen überschreiben die Standarddateien des übergeordneten Themes.

## Fazit

Durch die Anpassung von Theme-Templates, die Integration eigener Styles und Skripte sowie die Nutzung von Child-Themes können Webseiten individuell und nachhaltig gestaltet werden. Diese Ansätze ermöglichen es, spezifische Anforderungen umzusetzen, ohne dabei auf Updates oder neue Versionen des ursprünglichen Themes verzichten zu müssen.
