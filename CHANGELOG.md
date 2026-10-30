# Changelog

## 1.3.2

- Fix: saving a menu with invalid data (bad identifier, clash, empty title) now shows the validation message instead of a 500 (rollback outside a transaction).

## 1.3.1
- Template Hyvä: tolto `x-collapse` dai sottomenu del pannello mobile. Il plugin Collapse di Alpine non è incluso in Hyvä, quindi l'attributo non faceva nulla e riempiva la console del browser di avvisi (*You can't use [x-collapse] without first installing the "Collapse" plugin*). Nessun cambio di comportamento: i sottomenu si aprono e chiudono come prima.

## 1.3.0
- **Icona SVG accanto all'etichetta** di ogni voce (campi *Icona SVG*, *Posizione icona*, *Descrizione icona*). L'icona è un file `.svg` in `pub/media` (es. `wysiwyg/flag-it.svg`), letto, sanificato (via script, gestori `on*`, `foreignObject`, riferimenti esterni, entità) e inserito inline: eredita il colore del testo con `currentColor` ed è alta quanto il font. Un URL assoluto diventa un `<img>`. Senza descrizione l'icona è decorativa (`aria-hidden`), con descrizione ha `role="img"` e `aria-label`.
- Template Hyvä e template base mostrano l'icona prima o dopo l'etichetta, su tutti i livelli e nel mega menu. Le voci aggiunte da altri moduli senza le nuove chiavi continuano a funzionare.
- Nuove colonne `icon`, `icon_label`, `icon_position` in `threecommerce_menu_node` (nullable: i menu esistenti non cambiano).

## 1.2.0
- Template per temi Hyvä (`Threecommerce_Menu::hyva/menu.phtml`, Tailwind + Alpine): menu orizzontale con dropdown su desktop, pannello laterale con accordion su mobile, **mega menu** con colonne e blocco CMS/immagine a lato (si sposta da solo se uscirebbe dallo schermo), **badge** accanto all'etichetta, apertura in nuova scheda, pulsante per le voci con la classe `tcm-cta`, voce attiva marcata via JS. Argomenti del blocco `mobile_class`, `desktop_class`, `product_page_url`; colori semantici di Hyvä (`primary*`).

## 1.1.0
- Import da Snowdog estratto nel servizio `Threecommerce\Menu\Model\SnowdogImporter` (riusabile da data patch); il comando `threecommerce:menu:import-snowdog` lo usa. Le tabelle `snowmenu_*` restano nel database anche dopo la rimozione di Snowdog con Composer, quindi l'import funziona anche dopo.

## 1.0.0
- Primo rilascio: menu di navigazione gestiti da admin, un menu diverso per ogni store view, etichetta/URL/visibilità delle voci per store view, mega menu con blocco CMS e immagine, sottocategorie automatiche, import da Snowdog Menu.
