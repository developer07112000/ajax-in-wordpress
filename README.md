#step1 :
## Create the form  =====> your_form_page_name.php
```
<?php 
    /* Template Name: payment-template */
    get_header();
?>
<div class="container">
    <div class="payment-page-cooling-text">
    <p>
   Custom Form</p>
</div>
    <div class="payment-inner-section">
    <form method="post" action="" class="field-all-form">
         <div class="email-field">
            <label for="first_name_user">First Name</label>
            <input type="text" name="first_name_user" class="field-name-pay"/>
        </div>
         <div class="email-field">
            <label for="last_name_user">Last Name</label>
            <input type="text" name="last_name_user" class="field-last-pay"/>
        </div>
        <div class="email-field">
            <label for="email_forpay">Email</label>
            <input type="email" name="email_forpay" class="field-email-pay"/>
        </div>
        
        <div class="ammount-field">
            <label for="ammount_forpay">Amount (In USD)</label>
            <input type="text" name="ammount_forpay" class="field-ammount-pay"/>
        </div>
         <div class="email-field">
            <label for="pin_code_forpay">Zip Code</label>
            <input type="text" name="pin_code_forpay" class="field-pin-pay"/>
        </div>
        <div class="email-field">
            <label for="phone_num_forpay">Phone number</label>
            <input type="text" name="phone_num_forpay" class="field-phone-pay"/>
        </div>
        
        <input type="submit" value="Submit" name="btn_forpay" class="btn-submit-pay"/>
            
        <div class="data-output">
            <?php echo $output; ?>
        </div>
        
    </form>
    
</div>
    </div>
    
 
<?php
    get_footer();
?>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.6.3/jquery.min.js" integrity="sha512-STof4xm1wgkfm7heWqFJVn58Hm3EtS31XFaagaa8VMReCXAkQnJZ+jEy8PCC/iT18dFy95WcExNHFTqLyp72eQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-validate/1.19.5/jquery.validate.min.js" integrity="sha512-rstIgDs0xPgmG6RX1Aba4KV5cWJbAMcvRCVmglpam9SoHZiUCyQVDdH2LPlxoHtrv17XWblE/V/PP+Tr04hbtA==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>

<script type="text/javascript">

 jQuery(document).ready(function(){
jQuery(".field-all-form").validate({
rules: {
         first_name_user: "required", 
         last_name_user: "required", 
         email_forpay: {       
        required: true,
            email: true
         },
        ammount_forpay: {
        required: true
        },
        pin_code_forpay: "required",
        phone_num_forpay: {
        required: true,
        number: true
        }, 
     },
    messages: {
        first_name_user: "Enter your first name",
        last_name_user: "Enter your last name",
        email_forpay: "Enter a valid email address",
        ammount_forpay: "Please enter amount in numbers only",
        pin_code_forpay: "Enter zip code",
        phone_num_forpay: "Enter your mobile number",
     },
     submitHandler: function(form) {
        // event.preventDefault();
        var formData = { 
        first_name_user: jQuery(".field-name-pay").val(),
        last_name_user:  jQuery(".field-last-pay").val(),
        email_forpay:   jQuery(".field-email-pay").val(),
        ammount_forpay: jQuery(".field-ammount-pay").val(),
        pin_code_forpay: jQuery(".field-pin-pay").val(),
        phone_num_forpay: jQuery(".field-phone-pay").val(),
     }
        
    var first_name_user = jQuery(".field-name-pay").val();
    var last_name_user =  jQuery(".field-last-pay").val();
    var email_forpay =   jQuery(".field-email-pay").val();
    var ammount_forpay = jQuery(".field-ammount-pay").val();
    var pin_code_forpay = jQuery(".field-pin-pay").val();
    var phone_num_forpay = jQuery(".field-phone-pay").val();     
    var ajaxurl = "<?php echo admin_url('admin-ajax.php'); ?>";
        
      $.ajax({
      type: "POST",      
      url:ajaxurl,
        data: {
            action: 'payment_processing_data',
            first_name_user:first_name_user,
            last_name_user:last_name_user,
            email_forpay:email_forpay,
            ammount_forpay:ammount_forpay,
            pin_code_forpay:pin_code_forpay,
            phone_num_forpay:phone_num_forpay,
        },
        success:  function(response){
            alert('hli');
        
         console.log("---"+response);
     //   window.location.href = response;
// var removespace = response.replace(/&/g, '&');
// location.replace (removespace);
    }
       });
 }
});
});
 </script>

```
## Step2: Add the lines in the function.php
 ```
 add_action('wp_ajax_payment_processing_data', 'payment_processing_data');
add_action('wp_ajax_nopriv_payment_processing_data', 'payment_processing_data');
function payment_processing_data()
{
	
 $first_name_user = $_POST['first_name_user'];
 $last_name_user = $_POST['last_name_user'];
 $email_forpay = $_POST['email_forpay'];
 $ammount_forpay = $_POST['ammount_forpay'];
 $pin_code_forpay = $_POST['pin_code_forpay'];
 $phone_num_forpay = $_POST['phone_num_forpay'];

 
// CUSTOM CODE START HERE
//CUSTOM CODE END HERE	
}
```
##Step3: In function file  add_action( "wp_ajax_{your_function_name}",'your function name' )
## Step4: Action(In ajax code (jQuery)) Name and function name in function file are same.
