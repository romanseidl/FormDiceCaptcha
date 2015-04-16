# Dice Captcha
Processwire Dice Captcha Module

This is a simple Processwire Module.

@copyright 2015, Roman Seidl  
Licensed under GNU Lesser General Public License, Version 3, see LICENSE.TXT

![1](https://raw.githubusercontent.com/romanseidl/dice-captcha/master/DiceCaptcha/1.jpg) ![2](https://raw.githubusercontent.com/romanseidl/dice-captcha/master/DiceCaptcha/2.jpg) ![3](https://raw.githubusercontent.com/romanseidl/dice-captcha/master/DiceCaptcha/3.jpg) ![4](https://raw.githubusercontent.com/romanseidl/dice-captcha/master/DiceCaptcha/4.jpg) ![5](https://raw.githubusercontent.com/romanseidl/dice-captcha/master/DiceCaptcha/5.jpg) ![6](https://raw.githubusercontent.com/romanseidl/dice-captcha/master/DiceCaptcha/6.jpg)

This module allows you to ask a simple captcha question based on images of dice (6 sided). This could look as follows:
![screenshot](https://raw.githubusercontent.com/romanseidl/dice-captcha/readme/screen.png)

The shown dice are a temporary image that gets constructed on a first call. The correct answer is stored to the session. Just add a <img src='$dice->captcha()'/> to your form and check the input by using $dice->validate() after submit:
 
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
    
    <form method="post" action="./">
      <!--Show captcha -->
      <img src="$dice->captcha()"/>
      How much is the sum of the dice?
      <!--ask for sum -->
      <input type="text" name="captcha" value="$form[captcha]"/>
      <input type="submit" name="submit" value="submit">
    </form>

 

You are be able to change the image size and the number of dice in the module config interface.

If you want you can change the jpg files and adapt the size setting in the module accordingly. This should also increase security as if you use more complex images they will be harder to recognize. 

In case you want a pretty interface you could take pictures of real dice. If you want to try this I recommend you to take 6 dice and place them in a row against a white background. Then use some light source not too hard and not too close from the upper left (nw) corner (could be sunlight if you wait for the right time of the day) and take a picture. Don't use a wide angle lens as it will lead to inconsistencies between the dice. Then take this single image adjust color and contrast and cut out the dice into square images of the same size.

The result can look like this:  
![dice](https://raw.githubusercontent.com/romanseidl/dice-captcha/readme/dice.png)
