# intavia_scripts
Scripts for Intavia

## EDM conversion
These python notebooks are used to convert Europeana EDM creator and contributor data to Intavia Data Model (IDM). As input the script takes a list of intavia-wikidata sameas triples, the europeana metadata in various subfolders

### EDM cleaning
Using SWI-prolog, the following lines clean the unwanted triples:
?- forall((rdf(A,bioc:had_participant_in_role,R),not(sub_atom(R,_,_,_,'www.wikidata.org'))),(rdf_retractall(R,_,_),rdf_retractall(_,_,R))).
?- forall((rdf(A,bioc:had_participant_in_role,R),atomic_list_concat([_,WD],'producing_artist',R),atomic_list_concat(['http://',WD],WDU)),rdf_assert(A,ns1:'P11_had_participant',WDU)).
