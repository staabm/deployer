<!-- DO NOT EDIT THIS FILE! -->
<!-- Instead edit contrib/workplace.php -->
<!-- Then run bin/docgen -->

# workplace

[Source](/contrib/workplace.php)


## Installing

This recipes works with Custom Integrations and Publishing Bots.

Require the new recipe into your `deploy.php`

```php
require 'contrib/workplace.php';
```

Add hook on deploy:

```
before('deploy', 'workplace:notify');
```

## Configuration

 - `workplace_webhook` - incoming workplace webhook **required**
   ```
   // With custom integration
   set('workplace_webhook', 'https://graph.facebook.com/<GROUP_ID>/feed?access_token=<ACCESS_TOKEN>');

   // With publishing bot
   set('workplace_webhook', 'https://graph.facebook.com/v3.0/group/feed?access_token=<ACCESS_TOKEN>');

   // Use markdown on message
   set('workplace_webhook', 'https://graph.facebook.com/<GROUP_ID>/feed?access_token=<ACCESS_TOKEN>&formatting=MARKDOWN');
   ```

 - `workplace_text` - notification message
   ```
   set('workplace_text', '_{{user}}_ deploying `{{branch}}` to *{{target}}*');
   ```

 - `workplace_success_text` – success template, default:
  ```
  set('workplace_success_text', 'Deploy to *{{target}}* successful');
  ```
 - `workplace_failure_text` – failure template, default:
  ```
  set('workplace_failure_text', 'Deploy to *{{target}}* failed');
  ```
 - `workplace_edit_post` – whether to create a new post for deploy result, or edit the first one created, default creates a new post:
  ```
  set('workplace_edit_post', false);
  ```

## Usage

If you want to notify only about beginning of deployment add this line only:

```php
before('deploy', 'workplace:notify');
```

If you want to notify about successful end of deployment add this too:

```php
after('deploy:success', 'workplace:notify:success');
```

If you want to notify about failed deployment add this too:

```php
after('deploy:failed', 'workplace:notify:failure');
```



* Config
  * [`workplace_text`](#workplace_text)
  * [`workplace_success_text`](#workplace_success_text)
  * [`workplace_failure_text`](#workplace_failure_text)
  * [`workplace_edit_post`](#workplace_edit_post)
* Tasks
  * [`workplace:notify`](#workplacenotify) — Notifying Workplace
  * [`workplace:notify:success`](#workplacenotifysuccess) — Notifying Workplace about deploy finish
  * [`workplace:notify:failure`](#workplacenotifyfailure) — Notifying Workplace about deploy failure

## Config
### workplace_text
[Source](https://github.com/deployphp/deployer/search?q=%22workplace_text%22+in%3Afile+language%3Aphp+path%3Acontrib+filename%3Aworkplace.php)

Deploy message

### workplace_success_text
[Source](https://github.com/deployphp/deployer/search?q=%22workplace_success_text%22+in%3Afile+language%3Aphp+path%3Acontrib+filename%3Aworkplace.php)



### workplace_failure_text
[Source](https://github.com/deployphp/deployer/search?q=%22workplace_failure_text%22+in%3Afile+language%3Aphp+path%3Acontrib+filename%3Aworkplace.php)



### workplace_edit_post
[Source](https://github.com/deployphp/deployer/search?q=%22workplace_edit_post%22+in%3Afile+language%3Aphp+path%3Acontrib+filename%3Aworkplace.php)

By default, create a new post for every message


## Tasks
### workplace:notify
[Source](https://github.com/deployphp/deployer/search?q=%22workplace%3Anotify%22+in%3Afile+language%3Aphp+path%3Acontrib+filename%3Aworkplace.php)



### workplace:notify:success
[Source](https://github.com/deployphp/deployer/search?q=%22workplace%3Anotify%3Asuccess%22+in%3Afile+language%3Aphp+path%3Acontrib+filename%3Aworkplace.php)



### workplace:notify:failure
[Source](https://github.com/deployphp/deployer/search?q=%22workplace%3Anotify%3Afailure%22+in%3Afile+language%3Aphp+path%3Acontrib+filename%3Aworkplace.php)



