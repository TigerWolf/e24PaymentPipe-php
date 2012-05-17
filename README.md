e24PaymentPipe-php
==================

e24payment-php is an implementation in PHP of E24PaymentPipe  java classes. It allows to connect to online credit card payment from http://www.aciworldwide.com/ .

Gateways that use this include:
  - KNet - http://www.knet.com.kw/
  - Intesa San Paolo - http://www.intesasanpaolobank.al/
 

Example Usage
==================

      require_once('e24PaymentPipe.inc.php');
      $payment = new e24PaymentPipe;

      $payment->setErrorUrl("/application/error");
      $payment->setResponseURL("/application/success");

      $payment->setLanguage("ENG");
      $payment->setCurrency("840"); //USD
      $payment->setResourcePath('/e24payment/');
      $payment->setAlias("merchant-alias");
      $payment->setAction("1"); // 1 = Purchase

      $payment->setAmt($_POST['amount']);
      $payment->performPaymentInitialization();
      
      if (strlen($payment->getErrorMsg()) > 0) {
        echo $payment->getErrorMsg();
      }else{ 
        header('Location: ' . $payment_id = $payment->paymentPage . '?PaymentID=' . $payment->paymentId);
      }
      
Requirements
=================

This requires php 5.3 in order to work.

Userful Links
================

http://www.logisticsworld.com/currency.asp - Find your currency code here.

Credits
================

This library origonally written by Paolo Carlo Pomi, that had not been updated since 2009. It did not work with php 5. I have removed a dependency that it had with "pclzip.lib.php" and used the native php 5 functionality for zip.