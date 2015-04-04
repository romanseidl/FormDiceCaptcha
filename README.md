# dice-captcha
Processwire Dice Captcha Module

This is a simple Processwire Module.

@copyright 2015, Roman Seidl
Licensed under GNU/GPL v3, see LICENSE.TXT

![1](https://raw.githubusercontent.com/romanseidl/dice-captcha/master/DiceCaptcha/1.jpg) ![2](https://raw.githubusercontent.com/romanseidl/dice-captcha/master/DiceCaptcha/2.jpg) ![3](https://raw.githubusercontent.com/romanseidl/dice-captcha/master/DiceCaptcha/3.jpg) ![4](https://raw.githubusercontent.com/romanseidl/dice-captcha/master/DiceCaptcha/4.jpg) ![5](https://raw.githubusercontent.com/romanseidl/dice-captcha/master/DiceCaptcha/5.jpg) ![6](https://raw.githubusercontent.com/romanseidl/dice-captcha/master/DiceCaptcha/6.jpg)

If you want you can change the jpg files and adapt the size setting in the module accordingly. This should also increase security as if you use more complex images they will be harder to recognize.
You can als change the number of dices asked for.

Usage:

    <?php
    //Init Module
    $dice = $modules->get("DiceCaptcha"); 
    
    //On submit check if the validation is correct
    if($input->post->submit) {
        //validate - the value is stored in the session
        if(!$dice->validate($input->post->captcha)) 
          echo "<p class='error'>".__("Please check that you have completed all fields")."</p>";
        else
          echo "Success!";
    }
    
    ?>
    
    <form method="post" action="./">
      <!--Show captcha -->
      <img src="$dice->captcha()"/>
      How much is the sum of the dices?
      <!--ask for sum -->
      <input type="text" name="captcha" value="$form[captcha]"/>
      <input type="submit" name="submit" value="submit">
    </form>
