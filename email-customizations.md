# Translations in Vanilla

### (especially emails)

---

`echo t('Some text to be translated', 'Optional fallback text');`

* In this example, 'Some text to be translated' is the translation key.
* Previously used 'slugs' for the first parameter.
* Now use abbreviated sentences for longer texts.

---

#[fit] More about translations

* Newlines matter!
* `%2$s` = second data paramenter (sprintf) & is a string (text).
* `{User.Name}` = `$this->data('User.Name')`
* Notice how few emails are represented in `locale/en.php`
* We basically have 2 email build systems: "entry" and "activity"

--- 

```
$Definition['EmailHeader'] = 'Hello {User.Name}!
';
$Definition['EmailFooter'] = '
Have a great day!';

// $Definition['EmailInvitation'] = 'Hello! ...

// $Definition['EmailMembershipApproved'] = 'Hello %1$s, ...

// $Definition['EmailPassword'] = '%2$s has reset your password ...

// $Definition['EmailConfirmEmail'] = ...
```
---

```
$Definition['EmailWelcomeRegister'] = 'You have successfully
registered for an account at {Title}. Here is your information:

  Username: {User.Name}
  Email: {User.Email}

You can access the site at {/,exurl,domain}.';

$Definition['EmailWelcomeConnect'] = 'You have successfully 
connected to {Title}. Here is your information:

  Username: {User.Name}
  Connected With: {ProviderName}

You can access the site at {/,exurl,domain}.';
```

---
How we build the rest of our email notifications:

```
$Message = sprintf(
    $Story == '' ? 
        t('EmailNotification', "%1\$s\n\n%2\$s") :
        t('EmailStoryNotification', "%3\$s\n\n%2\$s"),
    $ActivityHeadline,
    ExternalUrl($Activity->Route == '' ? '/' : $Activity->Route),
    $Story
);
```
---
How we determine $ActivityHeadline (abbreviated):

```
$FullHeadline = t("Activity.{$Activity->ActivityType}.FullHeadline");
$ProfileHeadline = t("Activity.{$Activity->ActivityType}.ProfileHeadline");

// Set $MessageFormat to $ProfileHeadline if it's same user.
// Otherwise, use $FullHeadline.

return sprintf($MessageFormat, ... );
``` 
