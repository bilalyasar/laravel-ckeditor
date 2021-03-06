Laravel-CKEditor-Bundle
=======================

A Laravel 3.x bundle for integrating CKEditor in your applications.

## CKEditor Bundle, by Vilhjalmur Magnusson
CKEditor Bundle allows you to generate CKEditor rich text boxes for your Laravel applications.

######1. Install using Artisan CLI:

<pre>php artisan bundle:install ckeditor</pre>

######2. Add the following line to application/bundles.php file:

<pre>return array('ckeditor' => array('auto' => true),);</pre>

######3. Add the following to the application.php config file in the 'aliases' array:

<pre>'CKEditor'                 => 'CKEditor\\CKEditor',</pre>

######4. Publish the bundle assets to your public folder:

<pre>php artisan bundle:publish</pre>

######To create a super simple rich text box:

<pre>
$ckeditor = new CKEditor();
$ckeditor->editor('editorName');
</pre>

######To create a more advanced rich text box:

<pre>
$ckeditor = new CKEditor();
$config = array();
$config['toolbar'] = array(
    array( 'Source', '-', 'Bold', 'Italic', 'Underline', 'Strike' ),
    array( 'Image', 'Link', 'Unlink', 'Anchor' )
);
$events['instanceReady'] = 'function (ev) {
    alert("Loaded: " + ev.editor.name);
}';
$ckeditor->editor("field1", "<p>Initial value.</p>", $config, $events);
</pre>

If anyone wants to call an instance of the ckeditor statically then whom ever who has the knowledge and time and willing to do so can submit a pull-request when he/she has modified the ckeditor php class for those things. I however am not bothered by doing '$myeditor = new CKEditor();', and at the moment I am simply just not good enough a php programmer to accomplish the task. So any help and pull-requests are welcome.

######KCFinder integration:

IMPORTANT!
KCFinder use php $_SESSION, when you create $ckeditor = new CKEditor(); (second parameter can disable KCFinder)
$_SESSION['KCFINDER'] = array('disabled' => false); is set and KCFinder start to works.
Now user can upload files on server!
After user logout() you must use <b>session_destroy()</b> to disable KCFinder