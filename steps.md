we are training on "SAP Transportation management with bn4l " domain of SAP
till now we are doing hands on pratice

1. created a company code as "AVRC"
2. created a cost center as "AVRCCOS"
3. created a profit center  as "AVRCPRO"
4. Define of Material Management 
     - created plant code as "AVRC"
     -  created storage location as "AVRC"
     - created purchasing organisation as "AVRC"
      - Assign the Plant to the Company Code 
      - Assign the Purchase Organization to the Plant
5. Define sales and distribution
      - Created sales organisation as "AVRC"
      - Assign Sales Organization to Company Code
      - Assign Distribution Channel to Sales Organization
      - Assign Division to Sales Organization
      - Set Up the Sales Area
      - Assign Sales Organization / Distribution Channel to Plant
6. Define shipping point
     - Created shipping point as "AVRC"
     - Assign shipping point to plant 
     - Shipping Point Determination Backend Logic

7. Created purchasing group as "AVRC"
8. Created organisational model 
     - created organisational model "AVRC" with 24 company(org unit function) and 1 organisation (org unit role) In respective columns
    - created purchase org under AVRC as 2 purchasing and 1 organisation as same above cloums
     - created purchase group under AVRC as 2 purchasing and 3 groups as same above cloumns
 
9. Activation of ledger plant(omx3,omx2,omx1,CKMSTART)
10. creation of material master(mm01)
     in material master only we define gross weight and net weight as 500 and 450
11. Creation of BP (customer and carrier)
    - customer = BP (00000)-> Customer(FLCU00) ->customer (FLCU01)
    - carrier  =  BP(00000) -> Supplier(FLVN00) -> Supplier(FVLVN01) -> Carrier(CRM010)
12. Define Logistics integration profile
     - created LIP as "AVRC" (FUBR AS "AVRC_FUBR")
     - Define Transportation relevance of sales Document
13. create fubr as "AVRC_FUBR"
     - here we give split quantity as 2000
14. create a sales order 
       - in sold to party we have BP as customer and same as ship to party
15. we created frieght unit type as "AVRU""
      - edit fubr and go to preivously created fubr in that document type keep frieght unit type "AVRU"
      - again we created another sales order 
      - here we divide frieght unit types as above mentioned split quantity and give qauntity as 10 
      - so that 500(gross weight)*10(quantity)=5000 weight 
      - it divided into 3 frieght unit types as 2000,2000,1000beacise we give split quantity as 2000
16. created frieght order type as "AVRO"
17. create means of transport and resources of their means of transport 
       - mot= TRUCK_AVRC
       - resouces as BOXTRUCK,FLATBED,TANK 3 types are connected to Means of tarnsport "TRUCK_AVRC".
note: WE are extracting source location and destination loaction  by displaying frieght unit type
18. define transportation lanes(/n/SCMTMS/TL5)(connecting means of transport to carrier)
19. define transportation zones (/n/SCMTMS/ZONE)(AV_ZONE1,AV_ZONE2)(defining souce and destination loactions as zones)
20. Goto Firori screen Create selection profile 
     - selection profile 
    - time related selected attributs 
    - geographical selection attributes 
    - additional selection attributes 
21. Planning Profile
   - Planning profile
 
22. page layout for TC (used pre defined) 
23. Profile and Layout settings (Profile and settings)  
24. go to planning -> transportation cockpit 



### TCM(Transportation Charge Management)
- We are following Bottom -Up Approach
- Frieght Settlement Document(Calculation in Frieght order / Frieght booking )
- Goto Charge management
11. Create scale
    - AV_LOC(AVRC source location) as LOC 
    - AA_LOC(AVRC Destination location) as LOC
    - AV_GROSSWeight (AVRC Gross weight) as Weight 
12. create rate table Definition
    - Define rate table types
      SPRO -> sap img ref -> TM -> Master data -> Rate Tables -> Define Rate table type 
      (AVRC)
      
    - Define Charge Types 
       SPRO -> sap img ref -> TM -> Basic functions -> Charge calculation -> basic settings -> Define charge Types 
       (AVRC_BASEFRT) 

    - create rate table definition(Friori screen) 55 mins 
       (RT_AVRC) 
       . General Data -> insert scales 
    

13. Charge calucation sheet - create calculation sheet 
    - AVRC_TCCS
  
14. Frieght agreement
     SPRO -> sap img ref -> TM -> master data -> Agreement and service product -> define frieght Agreement Types 
     (AVRC - Frieght agreement type)

    - Create Frieght Agreement (Contract manager) 
    - calculate charges and till here we done 


