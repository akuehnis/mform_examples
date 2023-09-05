# Beispield für Redaxo Plugin MForm Version 7

 ## Redactor-Editor
 Input
 ```
<?php 
$mform = Mform::factory();
$mform->addTextareaField(1, [
    'label' => 'Inhalt',
    'class' => 'form-control redactor-editor--full']);
echo $mform->show();
?>
```

Output
```
REX_VALUE[id="1" output="html"]
```


 ## Interne Weiterleitung

 Input
 ```
<?php
$mform = Mform::factory();
$mform->addLinkField(1, ['label' => 'Zielseite']);
echo $mform->show();
?>
```

Output
```
<?php
if (rex::isBackend()):?>
  Weiterleitung zu <a href='index.php?page=content&article_id=REX_LINK[id=1]&mode=edit'>Artikel REX_LINK[id=1]</a>
<?php elseif ('REX_LINK[id=1]'): 
  $url = rex_getUrl('REX_LINK[id=1]');
  header("Location: $url");
  die();
else: ?>
  Fehler bei der Weiterleitung
<?php endif;?>
```
