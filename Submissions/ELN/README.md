# Electronic Laboratory Notebook (ELN) Format


**Format name**

Electronic Laboratory Notebook (ELN)

**Version number**

n/a

**Extensions**

`eln`

**MIME/Media Type**

https://www.iana.org/assignments/media-types/application/vnd.eln+zip

**Description**

A zip container file for the exchange of experimental results and data.

**Format type**

Aggregate

**Vendor**

The specification is freely available via https://github.com/TheELNConsortium/TheELNFileFormat. It follows the RO-Crate specification https://www.researchobject.org/ro-crate/specification.html, which specifies that 

- the root dir must contain a file called `ro-crate-metadata.json` 
- which contains the string `https://w3id.org/ro/crate/` near the beginning

The difference to other RO-Crate packages is that

- the files must be bundled into a ZIP archive
- which must have the extension `eln`

The file format is supported by a variety of applications, see the ELN specification above.


**File format identification signatures**

```xml
<ContainerSignature Id="1000" ContainerType="ZIP">
   <Description>Electronic Laboratory Notebook (ELN) Format</Description>
   <Files>
    <File>
     <Path>ro-crate-metadata.json</Path>
     <BinarySignatures>
      <InternalSignatureCollection>
       <InternalSignature ID="300">
        <ByteSequence Reference="BOFoffset">
            <SubSequence MinFragLength="11.5" Position="1" SubSeqMaxOffset="32" SubSeqMinOffset="9">
          <Sequence>'https://w3id.org/ro/crate/'</Sequence>
         </SubSequence>
        </ByteSequence>
       </InternalSignature>
      </InternalSignatureCollection>
     </BinarySignatures>
    </File>
   </Files>
  </ContainerSignature>
 ```
 
**Relevant links, documentation, extra information**

Any links to where you found your information, or anything else you think is important not yet covered.

**Credit**

Landesinitiative LZV.nrw / Hochschulbibliothekszentrum NRW (hbz)