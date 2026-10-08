# Electronic Laboratory Notebook (ELN) Format


**Format name**

Electronic Laboratory Notebook (ELN)

**Version number**

- 1.1 (TBC, all files created before the initial stable ELN Specification 1.2+20260923 was published)
- 1.2

**PUID**

new format

**Extensions**

`eln`

**MIME/Media Type**

https://www.iana.org/assignments/media-types/application/vnd.eln+zip

**Description**

A zip container file for the exchange of experimental results and data.

**Format type**

Aggregate

**Vendor**

The specification follows the RO-Crate specification https://www.researchobject.org/ro-crate/specification.html. It is freely available via https://github.com/TheELNConsortium/TheELNFileFormat and specifies that 

- the file must be a zip container
- the zip file must contain a variably named directory, which must contain a file called `ro-crate-metadata.json` 
- which must contain the string `https://w3id.org/ro/crate/`

In Version 1.1 the difference to other zipped RO-Crate packages (which may also contain a variably named directory, in which the file called `ro-crate-metadata.json` is located) is that

- the files must have the extension `eln`

Version 1.2 additionally introduces an ID:

- The ID is `https://purl.archive.org/purl/elnconsortium/eln-spec/1.2+20260923` which allows a strong signature.
- TBC if the signature should omit the last part `+20260923` as this may change often, or only changes together with the previous part.

The file format is supported by a variety of applications, see the ELN specification above.


**File format identification signatures**

Version 1.1:

```xml
<ContainerSignature Id="1000" ContainerType="ZIP">
   <Description>Electronic Laboratory Notebook (ELN) Format</Description>
   <Files>
    <File>
     <Path>*/ro-crate-metadata.json</Path>
     <BinarySignatures>
      <InternalSignatureCollection>
       <InternalSignature ID="300">
        <ByteSequence Reference="Variable">
         <SubSequence Position="1">
           <Sequence>'https://w3id.org/ro/crate/1.'(31|32)</Sequence>
         </SubSequence>
        </ByteSequence>
       </InternalSignature>
       <!-- one example file (created by elabftw) has backslashes -->
       <InternalSignature ID="400">
        <ByteSequence Reference="Variable">
         <SubSequence Position="1">
          <Sequence>'https:\/\/w3id.org\/ro\/crate\/1.'(31|32)</Sequence>
         </SubSequence>
        </ByteSequence>
       </InternalSignature>
      </InternalSignatureCollection>
     </BinarySignatures>
    </File>
   </Files>
  </ContainerSignature>
 ```
 
 Version 1.2:

 ```xml
 <ContainerSignatures>
  <ContainerSignature Id="1002" ContainerType="ZIP">
   <Description>Electronic Laboratory Notebook (ELN)</Description>
   <Files>
    <File>
     <Path>*/ro-crate-metadata.json</Path>
     <BinarySignatures>
      <InternalSignatureCollection>
       <InternalSignature ID="300">
        <ByteSequence Reference="Variable">
         <SubSequence Position="1">
          <Sequence>'https://purl.archive.org/purl/elnconsortium/eln-spec/1.2'</Sequence>
         </SubSequence>
        </ByteSequence>
       </InternalSignature>
      </InternalSignatureCollection>
     </BinarySignatures>
    </File>
   </Files>
  </ContainerSignature>
 </ContainerSignatures>
 ``` 


**Relevant links, documentation, extra information**

The ro-crate-metadata.json file is inside a variably named folder. Tyler helped out, suggesting the glob matching solution (see https://github.com/digital-preservation/pronom/issues/10), which seems to work. 

**Credit**

Landesinitiative LZV.nrw / Hochschulbibliothekszentrum NRW (hbz)


# open questions

- [ ] Version 1.1: This signature works but it could be called 'weak' as there will be other RO-Crate packages where folders containing the ro-crate-metadata.json file have been zipped, resulting in false posiives. (Unfortunately the .eln extension can not be used as part of the signature.) Should it still be submitted as ELN v1.1? Alternatively, does it make more sense to submit an entry for RO-Crate, and in the description for that entry explain that there is a subtype with the file extension .eln, together with a link to the ELN spec? (Assuming that RO-Crate could legitimately be called a file format. Apparently it's more a way to structure a range of files and folders, so that the sometimes large binary files within can be worked on, without necessarily putting them into a container. ELN on the other hand is explictly designed to be an exchange and storage format.)
- [ ] The ELN consortium has recently added an identifier (https://github.com/TheELNConsortium/TheELNFileFormat/issues/161), and this first stable version is called 1.2. In my understanding (all?) previous versions of the file should be called v1.1. I'll try to confirm this with the consortium. Also the question how often they expect the format spec to change, and if the date stamp at the end changes independently (and more often) or always together with the 1.x version number.

