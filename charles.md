# Charles Proxy Setup (Windows + Chrome)

This guide covers installing Charles, trusting its root certificate, and enabling SSL proxying so you can read HTTPS traffic from Chrome.

> **Note:** Charles is paid software with a limited free trial (check the current terms on their site). Installing its root certificate lets Charles decrypt your HTTPS traffic, so remove the certificate when you no longer need it. Only intercept traffic from apps and sites you're authorized to test.

## 1. Download Charles

Go to the [Charles website](https://www.charlesproxy.com/), open the [download page](https://www.charlesproxy.com/download/), and download the version for your OS.

<img width="899" height="537" alt="Charles download page" src="https://github.com/user-attachments/assets/140bf47c-2c9b-4734-953f-c20a7c366d88" />

## 2. Use v4.6.8 (optional)

I'm using **v4.6.8**, because with the latest version I ran into issues while installing the certificate. If you hit the same problem, get it from the [previous releases](https://www.charlesproxy.com/download/previous-release/) page.

<img width="849" height="465" alt="Charles previous releases page" src="https://github.com/user-attachments/assets/0d5bc419-e8ec-4021-8711-489d46a88e7e" />

## 3. Install the Charles root certificate

After installing Charles, the next crucial step is to install its root certificate and make Chrome trust it. Without this, HTTPS traffic can't be decrypted.

In Charles, go to **Help → SSL Proxying → Install Charles Root Certificate**.

<img width="939" height="445" alt="Charles Help menu, SSL Proxying, Install Charles Root Certificate" src="https://github.com/user-attachments/assets/53adbe8e-c7b1-46a0-bfa1-86be8aed048b" />

## 4. Import the certificate into the Windows trust store

After clicking **Install Charles Root Certificate**, a certificate window opens. (My screenshots may look slightly different because I had already installed the certificate.)

1. Click **Install Certificate**.
2. Select **Current User**.
3. Select **Place all certificates in the following store**.
4. Click **Browse** and choose **Trusted Root Certification Authorities**, so the certificate is placed in the trusted folder.
5. Click **Next**, then **Finish**. You should see a message saying the import was successful.

<img width="556" height="551" alt="Certificate window, Install Certificate" src="https://github.com/user-attachments/assets/be354a2f-72e4-404b-97c1-a68671a32874" />
<img width="576" height="532" alt="Certificate import wizard, Current User" src="https://github.com/user-attachments/assets/6303fbda-2bc5-436e-813e-c88fea2212db" />
<img width="531" height="514" alt="Certificate import wizard, choose store" src="https://github.com/user-attachments/assets/595978ba-845f-4fe8-8f0d-46c0c9ccc0db" />
<img width="531" height="507" alt="Selecting Trusted Root Certification Authorities" src="https://github.com/user-attachments/assets/29490036-e619-4d22-b14b-d3abb76a92b4" />
<img width="525" height="515" alt="Certificate import wizard, Finish" src="https://github.com/user-attachments/assets/9f5f23fb-7b44-466e-bddc-1fd1b974d87f" />
<img width="305" height="219" alt="Import successful message" src="https://github.com/user-attachments/assets/2b72dfcd-9199-49a1-ad9a-af8369777b1e" />

## 5. Add the certificate to Chrome (if needed)

Chrome on Windows usually trusts certificates from the Windows store, so step 4 may already be enough. If Chrome still shows certificate warnings, save the certificate from **Help → SSL Proxying → Save Charles Root Certificate**, then add it in `chrome://certificate-manager/` under **Trusted Certificates**.

## 6. Verify the certificate installation

Before intercepting, make sure the certificate was installed correctly. Without it, interception won't work. Open any HTTPS site in Chrome: there should be no certificate warning, and the request should appear in Charles.

<img width="403" height="527" alt="Verifying the certificate installation" src="https://github.com/user-attachments/assets/500638f4-fc8c-4fb0-b33a-34a6a0daddeb" />

## 7. Enable SSL proxying

Go to **Proxy → SSL Proxying Settings** and add the domain as shown below.

Without SSL proxying enabled for a host, Charles can't decrypt its traffic, so headers and bodies stay unreadable. To capture all hosts, add `*:443`, though this can be noisy.

<img width="526" height="538" alt="Proxy menu, SSL Proxying Settings" src="https://github.com/user-attachments/assets/ced164b8-c0ed-4973-9b26-fcccaff037ed" />
<img width="701" height="443" alt="Adding a domain to SSL proxying locations" src="https://github.com/user-attachments/assets/c3529a02-f9a3-4ffd-b60e-63c305f1055c" />

## 8. Enable HTTP/2 support

Go to **Proxy → Proxy Settings** and check the port. Make sure **Support HTTP/2** is enabled. Most sites now use HTTP/2, and without this you'll only capture HTTP/1.1.

<img width="669" height="498" alt="Proxy settings with Support HTTP/2 enabled" src="https://github.com/user-attachments/assets/80be3b54-4c51-444c-a5c1-21cab8dfdc4e" />

## 9. Make sure Charles is set as the system proxy

Make sure Charles is registered as the system proxy on its local port (8888 by default). It usually does this automatically (**Proxy → Windows Proxy**), but if no traffic shows up, check that the proxy is enabled and the port matches.

<img width="530" height="481" alt="Proxy settings showing localhost and port" src="https://github.com/user-attachments/assets/94bc4d64-a236-4175-a59e-9277cb1aa6dd" />

## Done 🎉

You can now start intercepting traffic and inspect headers, requests, TLS info, and more.

<img width="817" height="612" alt="Charles showing intercepted request details" src="https://github.com/user-attachments/assets/fa9dc4c3-3f4d-42de-8e0f-90e9c990b430" />

> 📚 For more info, refer to the [official Charles installation docs](https://www.charlesproxy.com/documentation/installation/), or open an issue / tag me [@rajputpriyankaa](https://github.com/rajputpriyankaa).
