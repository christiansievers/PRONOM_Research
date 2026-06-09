# New file format: QLab

Extension(s):
cues, qlab4, qlab5

MIME/Media Types:
Unsure 

Description:
Show control system file format. QLab is a piece of macOS software for designing and playing back sound, video, light, and show control cues. It is commonly used in theatre productions. For versions 1-3 the extension .cues was used. For version 4 the extension is .qlab4, and for version 5 the extension is .qlab5. 

Reference(s):
https://qlab.app/ 

Signature(s):
62706C6973743030; 514C616253686F727456657273696F6E537472696E67

Signature description(s):
Absolute BOF: bplist00 (62706C6973743030)
Followed by: QLabShortVersionString (514C616253686F727456657273696F6E537472696E67) at a variable sequence position.

Currently QLab files are identified as Binary Property List format (fmt/984), but by adding the QLabShortVersionString signature, these can be disambiguated.

Samples for testing the signature:
https://drive.google.com/drive/folders/1cOQdtm0ahl0OmnXSRSdvBTrzf9AQWLNL 

Vendor/Support: 
Figure 53 - https://figure53.com/ 

Submitted by:
Nicola Caldwell
