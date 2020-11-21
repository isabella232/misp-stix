### MISP to STIX1

#### Events mapping

##### Summary

| MISP datastructure | STIX object|
| -- | -- |
| Event | `STIX Package` |
| Attribute | `Indicator` or `Observable` in most cases, `TTP`, `Journal entry` or `Custom Object` otherwise |
| Object | `Indicator` or `Observable` in most cases, `TTP`, `Threat Actor`, `Course of Action` or `Custom Object` otherwise |
| Galaxy | `TTP`, `Threat Actor`, or `Course of Action` |

##### Detailed mapping

The detailed mapping for events and its contained structures, with explanations and examples, is available [here](misp_events_to_stix1.md)

#### Attributes mapping

##### Summary

Most of the MISP attributes are converted into `Indicator` or `Observable` Objects.  
In the following table, all the object types preceded by any information about another object type are considered as being embedded in the list of `RelatedIndicators` or `RelatedObservables`.  
When they are exported neither as indicator nor as observable, the top level object type is mentioned.

| MISP Attribute type | STIX Object type - property name|
| -- | -- |
| AS | **ASObjectType** - Handle |
| attachment | **ArtifactObjectType** - Raw_Artifact |
| authentihash | **FileObjectType** - Hashes -> Hash - Simple_Hash_Value |
| cdhash | **FileObjectType** - Hashes -> Hash - Simple_Hash_Value |
| domain | **DomainNameObjectType** - Value |
| domain \| ip | ObservableComposition -> **DomainNameObjectType** - Value \| **AddressObjectType** - Address_Value |
| email-attachment | **EmailMessageObjectType** - Attachments *referencing* **FileObjectType** - File_Name |
| email-dst | **EmailMessageObjectType** - To -> **AddressObjectType** - Address_Value |
| email-src | **EmailMessageObjectType** - From -> **AddressObjectType** - Address_Value |
| email-reply-to | **EmailMessageObjectType** - Reply_To -> **AddressObjectType** - Address_Value |
| email-subject | **EmailMessageObjectType** - Subject |
| filename | **FileObjectType** - File_Name |
| filename \| authentihash | **FileObjectType** - File_Name \& Hashes -> Hash - Simple_Hash_Value |
| filename \| impfuzzy | **FileObjectType** - File_Name \& Hashes -> Hash - Simple_Hash_Value |
| filename \| imphash | **FileObjectType** - File_Name \& Hashes -> Hash - Simple_Hash_Value |
| filename \| md5 | **FileObjectType** - File_Name \& Hashes -> Hash - Simple_Hash_Value |
| filename \| pehash | **FileObjectType** - File_Name \& Hashes -> Hash - Simple_Hash_Value |
| filename \| sha1 | **FileObjectType** - File_Name \& Hashes -> Hash - Simple_Hash_Value |
| filename \| sha224 | **FileObjectType** - File_Name \& Hashes -> Hash - Simple_Hash_Value |
| filename \| sha256 | **FileObjectType** - File_Name \& Hashes -> Hash - Simple_Hash_Value |
| filename \| sha384 | **FileObjectType** - File_Name \& Hashes -> Hash - Simple_Hash_Value |
| filename \| sha512 | **FileObjectType** - File_Name \& Hashes -> Hash - Simple_Hash_Value |
| filename \| sha512/224 | **FileObjectType** - File_Name \& Hashes -> Hash - Simple_Hash_Value |
| filename \| sha512/256 | **FileObjectType** - File_Name \& Hashes -> Hash - Simple_Hash_Value |
| filename \| ssdeep | **FileObjectType** - File_Name \& Hashes -> Hash - Simple_Hash_Value |
| filename \| tlsh | **FileObjectType** - File_Name \& Hashes -> Hash - Simple_Hash_Value |
| filename \| vhash | **FileObjectType** - File_Name \& Hashes -> Hash - Simple_Hash_Value |
| hostname | **HostnameObjectType** - Hostname_Value |
| hostname \| port | **SocketAddressObjectType** - Hostname (**HostnameObjectType** - Hostname_Value) & Port (**PortObjectType** - Port_value)|
| http-method | **HTTPSessionObjectType** - HTTP_Method |
| impfuzzy | **FileObjectType** - Hashes -> Hash - Simple_Hash_Value |
| imphash | **FileObjectType** - Hashes -> Hash - Simple_Hash_Value |
| ip-dst | **AddressObjectType** - Address_Value |
| ip-dst \| port | **SocketAddressObjectType** - IP_Address (**AddressObjectType** - Address_Value) & Port (**PortObjectType** - Port_value) |
| ip-src | **AddressObjectType** - Address_Value |
| ip-src \| port | **SocketAddressObjectType** - IP_Address (**AddressObjectType** - Address_Value) & Port (**PortObjectType** - Port_value) |
| mac-address | **SystemObjectType** - Network_Interface_list -> Network_Interface - MAC |
| malware-sample | **ArtifactObjectType** - Raw_Artifact & Hashes -> Hash - Simple_Hash_Value |
| md5 | **FileObjectType** - Hashes -> Hash - Simple_Hash_Value |
| mutex | **MutexObjectType** - Name |
| named pipe | **PipeObjectType** - Name |
| pattern-in-file | **FileObjectType** - Byte_Runs -> Byte_Run - Byte_Run_Data |
| pehash | **FileObjectType** - Hashes -> Hash - Simple_Hash_Value |
| port | **PortObjectType** - Port_Value |
| regkey | **WindowsRegistryKeyObjectType** - Key |
| regkey \| value | **WindowsRegistryKeyObjectType** - Key & Values -> Value - Data |
| sha1 | **FileObjectType** - Hashes -> Hash - Simple_Hash_Value |
| sha224 | **FileObjectType** - Hashes -> Hash - Simple_Hash_Value |
| sha256 | **FileObjectType** - Hashes -> Hash - Simple_Hash_Value |
| sha384 | **FileObjectType** - Hashes -> Hash - Simple_Hash_Value |
| sha512 | **FileObjectType** - Hashes -> Hash - Simple_Hash_Value |
| sha512/224 | **FileObjectType** - Hashes -> Hash - Simple_Hash_Value |
| sha512/256 | **FileObjectType** - Hashes -> Hash - Simple_Hash_Value |
| snort | *indicator: Test_Mechanisms* -> **SnortTestMechanismType** - Rule |
| ssdeep | **FileObjectType** - Hashes -> Hash - Simple_Hash_Value |
| target-email | *incident: Victim* -> **CIQIdentity3.0InstanceType** - ElectronicAddressIdentifiers - ElectronicAddressIdentifier |
| target-external | *incident: Victim* -> **CIQIdentity3.0InstanceType** - PartyName - NameLine |
| target-location | *incident: Victim* -> **CIQIdentity3.0InstanceType** - Addresses -> Address - FreeTextAddress - AddressLine |
| target-machine | *incident: Affected_Assets* -> Affected_Asset - Description |
| target-org | *incident: Victim* -> **CIQIdentity3.0InstanceType** - PartyName -> OrganisationName - NameElement |
| target-user | *incident: Victim* -> **CIQIdentity3.0InstanceType** - PartyName -> PersonName - NameElement |
| tlsh | **FileObjectType** - Hashes -> Hash - Simple_Hash_Value |
| url | **URIObjectType** - Value |
| user-agent | **HTTPSessionObjectType** - HTTP_Request_Response -> HTTP_Client_Request -> HTTP_Request_Header -> Parsed_Header - User_Agent |
| vhash | **FileObjectType** - Hashes -> Hash - Simple_Hash_Value |
| vulnerability | *stix: TTPs* -> **TTPType** Exploit_Targets -> **ExploitTargetType** -> Vulnerability - CVE_ID |
| windows-service-displayname | **WindowsServiceObjectType** - Display_Name |
| windows-service-name | **WindowsServiceObjectType** - Service_Name |
| x509-fingerprint-md5 | **X509CertificateObjectType** - Certificate_Signature - Signature |
| x509-fingerprint-sha1 | **X509CertificateObjectType** - Certificate_Signature - Signature |
| x509-fingerprint-sha256 | **X509CertificateObjectType** - Certificate_Signature - Signature |
| yara | *indicator: Test_Mechanisms* -> **YaraTestMechanismType** - Rule |

##### Detailed mapping

The detailed mapping for attributes, with explanations and examples, is available [here](misp_attributes_to_stix1.md)

#### Objects mapping

##### Summary

| MISP Object name | STIX Object type |
| -- | -- |
|  |  |

##### Detailed mapping

The detailed mapping for objects, with explanations and examples, is available [here](misp_objects_to_stix1.md)

#### Galaxies mapping

##### Summary

| MISP Galaxy Clusters name | STIX Object type |
| -- | -- |
| android, backdoor, banker, malpedia, mitre-enterprise-attack-malware, mitre-malware, mitre-mobile-attack-malware, ransomware, stealer | *stix: TTPs* -> **TTPType** - Behavior -> Malware - Malware_Instance |
| botnet, exploit-kit, mitre-enterprise-attack-tool, mitre-mobile-attack-tool, mitre-tool, rat, tds, tool | *stix: TTPs* -> **TTPType** - Resources -> Tools -> Tool |
| branded-vulneratbility | *stix: TTPs* -> **TTPType** - Exploit_targets -> **ExploitTargetType** - Vulnerability |
| microsoft-activity-group, threat-actor | *stix: Threat_Actors* -> **ThreatActorType** |
| mitre-attack-pattern, mitre-enterprise-attack-attack-pattern, mitre-mobile-attack-attack-pattern, mitre-pre-attack-attack-pattern | *stix: TTPs* -> **TTPType** - Behavior -> Attack_Patterns -> Attack_Pattern |
| mitre-course-of-action, mitre-enterprise-attack-course-of-action, mitre-mobile-attack-course-of-action | *stix: Courses_Of_action* -> **CourseOfActionType** |


##### Detailed mapping

The detailed mapping for galaxies, with explanations and examples, is available [here](misp_galaxies_to_stix1.md)