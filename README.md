# wso2esb-passwordcallback
I keep having to search!!! So let's just save it in one place ;)

## The Vault

Mostly copied from here [http://soasecurity.org/2012/08/12/secure-plain-text-passwords-in-wso2-carbon-configuration-files/]

0. Stop Server
1. Configure passwords in **/repository/conf/security/cipher-text.properties**
2. Run **/bin/cipher-tool.\[bat|sh\] -DConfigure**, supplying **master password**
3. Start to confirm all is **OK**, this will ask for **master password**
4. Stop server
5. Replace all occurances of **org.wso2.carbon.securevault.DefaultSecretCallbackHandler**, with **com.sample.password.callback.handler.HardCodedSecretCallbackHandler**
6. Build project, in this repo, with **master password**. Maybe not the best, but you can call a Rest/Look for an environment variable, or anything you consider secure, to get the **master password**
7. Deploy built jar to **/repository/components/lib**
8. Start server, no password prompt should appear
