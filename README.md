# Q-SYS-BirdDog-FLEX-4K-Out

- BirdDog FLEX 4K IN Q-Sys User Component (REST API)
- Written by Glen Gorton
- Tested with Firmware version: BirdDog Flex_Out 4.5.158-LTS


## NOTES:
  
1. If a response string is corrupt it will contain %!s(<nil>). Within the Result() function I have added a check that if this is discovered it will SetStatus to compromised, then the pollTimer will start again after one hour.
"Settings Status with Code: '1', Message: 'Data response for query (decodesetup) from the device is corrupt: %!s(<nil>). May require a reboot or firmware reload."
Response example: {VideoSampleRate":"%!s(<nil>)","NDIAudio":"%!s(<nil>)}

2. "decodesetup" GET request response will include NDIAudio":"%!s(<nil>). Response from BirdDog: "That JSON key doesn't do anything for the Flex OUT. It is there because of how we reuse all the APIs across the flock. 
The reason why the initial value for it is NIL is because nothing has been written in there by the app, because it's not a setting that the app for the Flex OUT knows about (this is a feature not a bug)."
Response example: {"ColorSpace":"RGB","NDIAudio":"%!s(<nil>)","ScreenSaverMode":"BirdDogSS","TallyMode":"TallyOff"}
"decodesetup" response will not include a check for corrupt data within the Result() function.
