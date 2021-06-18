---
layout: post
title: Make custom configurations Translatable in Drupal
description: Requires content_translation module enabled.
date: '2020-05-22T15:35:23.787Z'
categories: []
keywords: []
migrated_source: 'Medium'
migrated_url: 'https://jaykandari.medium.com/make-custom-configurations-translatable-in-drupal-b57b7fdd71a5'
---

Requires **content\_translation** module enabled.

Start by creating a custom module create a folder “mymodule” and inside that module a new file: **mymodule.info.yml**

name: 'My module'  
description: 'Demonstrates making custom configs translatable.'  
type: module  
core\_version\_requirement: ^8.8 || ^9

Create a **mymodule.routing.yml file**.

mymodule.configure:  
 path: ‘/admin/config/mymodule/config’  
 defaults:  
 \_form: ‘Drupal\\mymodule\\Form\\MyModuleConfigForm’  
 \_title: ‘My Module configurations’  
 requirements:  
 \_permission: ‘administer site configuration’  
 options:  
 \_admin\_route: TRUE

Lets create a **mymodule.links.menu.yml** file:

mymodule.configure:  
 title: ‘My module configurations’  
 description: ‘Administer my module configurations.’  
 route\_name: mymodule.configure  
 parent: system.admin\_config

Create a task file **mymodule.links.task.yml**)so that the Translate tab is available on your route:

mymodule.configure:  
 base\_route: mymodule.configure  
 title: ‘My module settings’  
 route\_name: mymodule.configure

Create a schema file: .**/config/schema/mymodule.schema.yml**

mymodule.settings:  
 type: config\_object  
 label: ‘My module settings’  
 mapping:  
   name:  
     type: label  
     label: ‘Placeholder text’

Let config\_translation know which configuration & schema to map. Create a **mymodule.config\_translation.yml** file

mymodule.configure:  
  title: 'My module settings'  
  base\_route\_name: mymodule.configure  
  names:  
    - mymodule.settings

Let's create a default configuration file. .**/config/install/mymodule.settings.yml** :

name: '@JayKandari'

Finally, Let’s create a config form: .**/src/Form/MyModuleConfigForm.php**

<?php

namespace Drupal\\mymodule\\Form;

use Drupal\\Core\\Form\\ConfigFormBase;  
use Drupal\\Core\\Form\\FormStateInterface;

/\*\*  
 \* Mymodule config form.  
 \*/

class MyModuleConfigForm extends ConfigFormBase {  
  
  /\*\*  
   \* {[@inheritdoc](http://twitter.com/inheritdoc "Twitter profile for @inheritdoc")}  
   \*/  
  public function getFormId() {  
    return 'mymodule\_config\_form';  
  }  
  
  /\*\*  
   \* {[@inheritdoc](http://twitter.com/inheritdoc "Twitter profile for @inheritdoc")}  
   \*/  
  protected function getEditableConfigNames() {  
    return \['mymodule.settings'\];  
  }  
  
  /\*\*  
   \* {[@inheritdoc](http://twitter.com/inheritdoc "Twitter profile for @inheritdoc")}  
   \*/  
  public function buildForm(array $form, FormStateInterface $form\_state) {  
    $config = $this->config('mymodule.settings');

    $form\['name'\] = \[  
      '#type' => 'textfield',  
      '#title' => $this->t('Name'),  
      '#default\_value' => $config->get('name') ?? '@JayKandari',  
    \];

    return parent::buildForm($form, $form\_state);  
  }  
  
  /\*\*  
   \* {[@inheritdoc](http://twitter.com/inheritdoc "Twitter profile for @inheritdoc")}  
   \*/  
  public function submitForm(array &$form, FormStateInterface $form\_state) {  
    $values = $form\_state->getValues();  
    $this->config('mymodule.settings')  
      ->set('name', $form\_state->getValue('name'))  
      ->save();

    return parent::submitForm($form, $form\_state);  
  }

}

You are Done!!

Now go to **/admin/config/mymodule/config** to access your module configuration form.

And goto **/admin/config/mymodule/config/translate** to add config translations to your configurations.

Thanks for reading.
