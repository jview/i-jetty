# Getting Started #

![https://i-jetty.googlecode.com/svn/trunk/images/ijetty-launcher.png](https://i-jetty.googlecode.com/svn/trunk/images/ijetty-launcher.png)

After installing the i-jetty apk onto the phone, select the i-jetty application icon and click on it to activate:

![https://i-jetty.googlecode.com/svn/trunk/images/ijetty-screenshot.png](https://i-jetty.googlecode.com/svn/trunk/images/ijetty-screenshot.png)

## Stopping and Starting ##
### Start Jetty ###
Clicking the Start button will start an i-jetty service. i-jetty will be available on the phone at the port that you selected with the Configure button. The default port is 8080.

### Stop Jetty Button ###
The Stop Jetty button kills the i-jetty service. You will need to stop and then restart i-jetty for newly downloaded webapps to be deployed.

i-jetty will continue to run as a Service in the background once it is started. If you move away from the i-jetty application, you can always quickly return to it by selecting the i-jetty item in the status bar:

![https://i-jetty.googlecode.com/svn/trunk/images/ijetty-notification-screenshot.png](https://i-jetty.googlecode.com/svn/trunk/images/ijetty-notification-screenshot.png)

## Configuration ##

When i-jetty is stopped, click the Configure button:

![https://i-jetty.googlecode.com/svn/trunk/images/ijetty-configure-screen.png](https://i-jetty.googlecode.com/svn/trunk/images/ijetty-configure-screen.png)

Currently supported settings are:

### Http Connector ###

  * **Edit Port `[8080]`**
> > The port on which i-jetty will listen for requests.

  * **Use NIO `[true|false]`**
> > The default is true (since i-jetty-3.0). Select falseif you want i-jetty to use a blocking-style connector.


### Https Connector ###
  * **Use SSL `[false|true]`**
> > The default is false.Select true if you want i-jetty to ALSO start an SSL connector.

  * **Use NIO `[true|false]`**
> > The default is true (since i-jetty-3.0). Select false if you want i-jetty to use a blocking-style connector.

  * **Edit Port `[8443]`**
> > The port on which the SSL connector will listen for requests.

  * **Edit Password**
> > Enter a password ONLY if you are providing your own keystore.
> > This is the password that is passed to the KeyStoreManagerFactory.init()
> > method for the SslSocketConnector.


  * **Edit KeystoreManager Password**
> > Enter a password ONLY if you are providing your own keystore.
> > This is the password that is passed to KeyStore.load() method for
> > > the SslSocketConnector


  * **Edit Keystore Filename `[/sdcard/etc/keystore]`**

> > If you have a different keystore file, specify it here.


  * **Edit Truststore Filename `[/sdcard/etc/keystore]`**
> > If you are not using the i-jetty default, then specify the
> > location of your truststore here.

  * **Edit Truststore Password**
> > Enter a password ONLY if you are providing your own keystore.

**NOTE** that the SSL connector will by default use the same certificate as stand-alone Jetty. Your browser will warn you that the domain of the certificate does not match that of the server - this is expected. Configure your browser to accept the certificate, or alternatively use the configuration options to provide your own keystore.

Its worth noting that Android uses the BCK (BouncyCastle) format for the keystore, so you may need to convert your existing keystore first.

## Dynamic WebApp Download ##

The Download button allows you to dynamically download webapps that have been [prepared for Android](DownloadableWebapps.md):

![https://i-jetty.googlecode.com/svn/trunk/images/ijetty-download-screenshot.png](https://i-jetty.googlecode.com/svn/trunk/images/ijetty-download-screenshot.png)

Enter the **http url** of an android-enabled webapp. You can try this out using the "Hello World" webapp we supply at https://i-jetty.googlecode.com/p/i-jetty/downloads if you like.

Also enter the **context path** at which you want the web application to be deployed.  For example, for the "Hello World" webapp, you may want to deploy this at `/hello`. **Ensure that your context path starts with /**.

The webapp will be downloaded and installed to i-jetty. If i-jetty is already running, you will need to stop and restart in order to have the new webapp deployed.