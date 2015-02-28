#Awesome Bootstrap Checkbox for Yii2

Implementation of [Awesome Bootstrap Checkbox](https://github.com/flatlogic/awesome-bootstrap-checkbox/) within Yii2.

This extension overrides the ActiveField functions of `checkbox`, `radio`, `checkboxList`, and `radioList`.

Additionally, `CheckboxColumn` is included to implement the same awesome checkboxes in a GridView widget.

##Installation

###Install the extension

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
php composer.phar require --prefer-dist justinvoelker/yii2-awesomebootstrapcheckbox "*"
```

or add

```
"justinvoelker/yii2-awesomebootstrapcheckbox": "*"
```

to the require section of your `composer.json` file.

### Styles

Follow one of the directions below to use the styles necessary for awesome bootstrap checkboxes

#### Option 1: Manually combine stylesheets

Open your the `vendors\justinvoelker\yii2-awesomebootstrapcheckbox\css` directory and add the appropriate styles to your own stylesheet or include them in your less/scss files.

#### Option 2: Include the delivered asset bundle

Add `justinvoelker\awesomebootstrapcheckbox\Asset` as a dependency in your `assets\AppAsset` file. It should look similar to the following:

```php
public $depends = [
    'yii\web\YiiAsset',
    'yii\bootstrap\BootstrapAsset',
    'justinvoelker\awesomebootstrapcheckbox\Asset',
];
```

##Usage

###ActiveField

To use awesome bootstrap checkboxes in your ActiveForm, simply specify the `fieldClass` property of the ActiveForm as follows:

```php
$form = ActiveForm::begin([
    'fieldClass' => 'justinvoelker\awesomebootstrapcheckbox\ActiveField',
]);
```

Once the fieldClass is specified simply use checkbox, radio, checkboxList, or radioList as needed.  The following are some examples of usage.

```php
// Disabled checkbox with a customized label
$form->field($model, 'attribute')->checkbox(['label' => 'You cannot check this checkbox', 'disabled'=>true])

// Radio with the bootstrap primary color
$form->field($model, 'attribute')->radio(['divOptions' => ['class' => 'checkbox-primary']])

// List of disabled checkboxes 
$form->field($model, 'attribute')->checkboxList([1 => 'First', 2 => 'Second', 3 => 'Third'], ['itemOptions' => ['disabled' => true]])

// Inline list of enabled radio buttons with the bootstrap danger color
$form->field($model, 'attribute')->inline()->radioList([1 => 'First', 2 => 'Second', 3 => 'Third'], ['itemOptions' => ['disabled' => false, 'divOptions' => ['class' => 'radio-danger']]])
```

Keep in mind that at times there are essentially two labels for a given input: one for the entire field, one for that specific checkbox or radio button.  Specifying a label() will set the label for the entire field, specifying the `label` itemOption will change the label for a single checkbox() or radio() button.

###CheckboxColumn

To create a php array of key=>value pairs (where key is the tag and value is the frequency of that tag), use TaggingQuery:

```php
'columns' => [
    // ...
    [
        'class' => 'justinvoelker\awesomebootstrapcheckbox\CheckboxColumn',
        // you may configure additional properties here
    ],
]
```

An example of an additional property could be to limit the width of the checkbox column: `'contentOptions' => ['style' => 'width: 25px;'],`

##Credits
[Awesome Bootstrap Checkbox](https://github.com/flatlogic/awesome-bootstrap-checkbox/)
