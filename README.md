# Input-Masking-Directive
Input masking directive for angular apps<br/>

<h4>How to use!</h4>

The default selector for this directive is [appMask] 

this directive takes an attribute called MaskType <br/>
also, this directive emits all unmasked values <br/>
through an eventEmitter called "unmasked" 

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
 
the example function called on (unmasked) - <br/>
//snippet from my-component.ts<br/>
//takes a param to reference the data object which will 
//hold the emitted value <br/>
```js
checkUnmasked(data: any, event: Event) {
  //simply logs the emitted value 
  console.log(curString) 
}
```
  
so if we want to use multiple utilities of this directive we would <br/>
need to write multiple different functions to call on each (unmasked) event<br/>
  
ex:
  
//component.html
```html
<div class="ShortDate">
    <label for="ShortDate">Short Date</label>
    <br />
    <input appMask MaskType="shortDate" formControlName="ShortDate" (unmasked)="getShortDate($event)">
</div>

<div class="LongDate">
   <label for="LongDate">Long Date</label>
   <br />
   <input appMask MaskType="longDate" type="text" formControlName="LongDate" (unmasked)="getLongDate($event)">
</div>
```

//component.ts
```js
getShortDate(data: any, event: Event){
 console.log('short date', data);
}

getLongDate(data: any, event: Event){
 console.log('long date', data);
}
```

above shows us how to get each separate date that is being emitted!<br/><br/>

hopefully this was enough of an explanation. happy coding!


