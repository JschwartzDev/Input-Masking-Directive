# Input-Masking-Directive
Input masking directive for angular apps<br/><br/>

How to use!<br/><br/>

The default selector for this directive is [appMask] <br/><br/>

this directive takes an attribute called MaskType <br/>
and also, this directive emits all unmasked values <br/>
through an eventEmitter called "unmasked" <br/><br/>

first we should create an input that uses the appMask directive <br/>
and we need to asign that input a MaskType attribute with one of <br/>
the following values <br/>

/* <br/>
 "shortDate"      format: mm/yy  <br/>
 "longDate"       format: dd/mm/yyyy <br/>
 "phoneNumber"    format: (###) ###-#### <br/>
 "ssn"            format: ###-##-#### <br/>
 "shortZipCode"   format: ##### <br/>
 "longZipCode"    format: #####-#### <br/>
 "cardNumber"     format: #### #### #### #### (of variable length) <br/>
 "cvv"            format: ### or #### <br/>
 "dollarAmount"   format: $###.## (dollar amount of variable length) <br/>
*/<br/><br/>

our example input could look like <br/>

//snippet from my-component.html  <br/>
```html
<div class="ShortDate"> 
 <label for="ShortDate">Short Date</label>
    <br />
    <input appMask MaskType="shortDate" formControlName="ShortDate" (unmasked)="checkUnmasked($event)">
<div>
```
 //appMask to asign the directive <br/>
 //MaskType to tell the directive what type of input this is <br/>
 //(unmasked) property to grab the emitted values. <br/><br/>
 
 the example function called on (unmasked) - <br/><br/>
 
 //snippet from my-component.ts<br/>
 //takes a string reference which will hold the emitted value <br/>
 ```js
 checkUnmasked(curString: string, event: Event) {
    //simply logs the emitted value 
    console.log(curString) 
  }
  ```
