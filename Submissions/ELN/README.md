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

- the file must be a zip container
- the zip file contains a variably named directory, which must contain a file called `ro-crate-metadata.json` 
- which must contain the string `https://w3id.org/ro/crate/1.1`

The difference to other zipped RO-Crate packages is that

- the files must have the extension `eln`

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
 


**Relevant links, documentation, extra information**

The ro-crate-metadata.json file is inside a variably named folder. Tyler helped out, suggesting the glob matching solution (see https://github.com/digital-preservation/pronom/issues/10), which seems to work. 

**Credit**

Landesinitiative LZV.nrw / Hochschulbibliothekszentrum NRW (hbz)


# open questions

- [ ] This signature works but it could be called 'weak' as there will be other RO-Crate packages that have been zipped. The signature could add the condition that the file must have the .eln extension (which wouldn't be ideal). 
- [ ] I'm in touch with the ELN consortium about the problem that the only way to distinguish other zipped RO-Crate packages from ELN is the extension.  The consortium is considering adding an identifier (https://github.com/TheELNConsortium/TheELNFileFormat/issues/161), but that would only work forward, once the various applications that can write ELN implement this. Should we wait for the new version of the spec, or should this signature be submitted?

- [ ] one of the example files (examples/elabftw/export.eln) contains backslashes in the string: `https:\/\/w3id.org\/ro\/crate\/`. Should I remove ByteSequence, so that it only looks for the file? Or add another ByteSequence with this string, i.e. in hex so that it's less troublesome `68 74 74 70 73 3a 5c 2f 5c 2f 77 33 69 64 2e 6f 72 67 5c 2f 72 6f 5c 2f 63 72 61 74 65 5c 2f` ?

