# Electronic Laboratory Notebook (ELN) Format


**Format name**

Electronic Laboratory Notebook (ELN)

**Version number**

n/a

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
     <Path>*/ro-crate-metadata.json</Path>
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
 
- [ ] ==one of the example files (examples/elabftw/export.eln) contains https:\/\/w3id.org\/ro\/crate\/ - remove ByteSequence, so that it only looks for the file? or add anoher ByteSequence?==

- [ ] ==There will be other RO-Crate packages that have been zipped. So the only way to distinguish those from ELN is the extension -> add condition that the file must have the .eln extension?==


**Relevant links, documentation, extra information**

The ro-crate-metadata.json file is inside a variably named folder. Tyler helped out, suggesting the glob matching solution (see https://github.com/digital-preservation/pronom/issues/10), which seems to work. 

**Credit**

Landesinitiative LZV.nrw / Hochschulbibliothekszentrum NRW (hbz)