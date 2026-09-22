# Wireshark Installation guide on macOS 

## Step 1 : Download Wireshark

Go to the official Wireshark website. Click on the blue button called **Download Now**.

<img width="1024" height="508" alt="image" src="https://github.com/user-attachments/assets/01c74266-013c-4ae8-afd6-f86e80d321ba" />

Click on **macOS Universal Disk Image**.

<img width="704" height="524" alt="image" src="https://github.com/user-attachments/assets/89e19c23-07f3-458c-9634-3afcd1bc40af" />


## Step 2 : Installation

1. Open the file you just downloaded 
2. Move the file into your apps **Applications**.
3. Open Wireshark from your applications.

**⚠️**
You will probably have a message the first time you are loading the app. The message should say "You don't have permission to capture on local interfaces".
In order for Wireshark to work well, you need to click on the blue link **"installing ChmodBPF"**. It will install a little script that autorize the Mac to listen to the network.


<img width="2094" height="1318" alt="image" src="https://github.com/user-attachments/assets/e3f980a4-4974-4487-88e0-bedfcb9549d4" />


## Step 3 : Start 

When ChmodBPF is installed, you can start to use Wireshark. 

Choose the network you want to see (usually it's gonna be **Wi-Fi: en0**).


<img width="1024" height="620" alt="image" src="https://github.com/user-attachments/assets/b2342a07-a7a3-408d-b8d4-1cd8f3579107" />

That's it ! Good luck :) 

```eof

