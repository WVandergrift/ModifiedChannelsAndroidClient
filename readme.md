# How to modify the Channels App to enable the API on any device

1. Use apktool to decompile the app
    ```
    apktool d channels.apk
    ```
2. Open the ChannelsApp.smali file
    ```
    smali/com/getchannels/android/ChannelsApp.smali
    ```
3. Remove the two conditions for starting the API server
    ```
    4068: if-nez v1, :cond_0
    4080: if-eqz v1, :cond_2
    ```
4. Build the apk
    ```
    apktool b /Path/to/channels/code
    ```
5. Sign the apk (uber-apk-signer makes it simple)
    ```
    java -jar uber-apk-signer.jar --apks /Path/to/modified/channels.apk
    ```
6. Install the apk on your device
    ```
    abd install /Path/to/signed/channels.apk
    ```
