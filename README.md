# Input-Masking-Directive
Input masking directive for angular apps

How to use!

The default selector for this directive is [appMask] 

this directive takes an attribute called MaskType 
and also, this directive emits all unmasked values
through an eventEmitter called "unmasked"

first we should create an input that uses the appMask directive
and we need to asign that input a MaskType attribute with one of 
the following values

/*
 "shortDate"      format: mm/yy  
 "longDate"       format: dd/mm/yyyy
 "phoneNumber"    format: (###) ###-####
 "ssn"            format: ###-##-####
 "shortZipCode"   format: #####
 "longZipCode"    format: #####-####
 "cardNumber"     format: #### #### #### #### (of variable length)
 "cvv"            format: ### or ####
 "dollarAmount"   format: $###.## (dollar amount of variable length)
*/

our example input could look like 

<!--snippet from my-component.html-->
<div class="ShortDate">
    <label for="ShortDate">Short Date</label>
    <br />
    <input appMask MaskType="shortDate" formControlName="ShortDate" (unmasked)="checkUnmasked($event)">
</div>

 //appMask to asign the directive
 //MaskType to tell the directive what type of input this is
 //(unmasked) property to grab the emitted values.  
 
 the example function called on (unmasked) -
 
 <!--snippet from my-component.ts-->
 //takes a string reference which will hold the emitted value
 checkUnmasked(curString: string, event: Event) {
    //simply logs the emitted value
    console.log(curString)
  }
