# uml-model
UML Model and XMI graph model for UML

## Shape Expressions
The UML model can be exported as [ShEx](http://shex.io/).
Where a UML model describes classes which can be instantiated with some binding to a format (e.g. XML, ASN-1, RDF), the ShEx specifically describes and tests conformance of RDF data.
Choices have to be made when mapping context-sensitive UML attribute names to context-free RDF property names.
OMG's [ODM 1.1](https://www.omg.org/spec/ODM/About-ODM/) section 11 takes a conservative approach by mapping each UML class attribute to a unique RDF property whose identifier includes the name of the containing class and the name of the property.
For instance, in BRIDGE/RDF, which uses the ODM UML-to-OWL mapping, the UML class `SubjectIdentifier` has a property `typeCode`, and this is represented by the rdf property `bridg:SubjectIdentifier.typeCode`.
This conservative approach is necessary for models with no coordination of property names.
For example, in FHIR, the HL7 Core FHIR Resources are modeled by different communities with domain expertise.
Other modeling efforts, like DDI, deliberately re-use property names on different classes in order to capture a common semantics.
For instance, in DDI, `Image` and `ExternalMaterial` (and other classes) share a common `uri` property.
This mapping of UML to ShEx assumes the latter model.
It's possible that this code will be expanded to perform either mapping, depending on an invocation switch.
