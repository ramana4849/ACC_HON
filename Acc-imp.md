### Topics he covered 

1. OBY6 - to check all company codes
#### Creation of company code 

- SPRO -> SAP Image REF 

- Enterprise Structure -> Definition -> Financial Accounting -> Edit,copy,delete and check company code 

example:

from company code: 4001 0R 1404
to company code: THSC or PNRC or AVRC OR RSBP

```


- click create request and edit description 
- CHANGE COMPANY NAME
- check company code with OBY6.


#### Creation of cost and profit center 
- creation of profit center(ke51)

    ```
   example:
   PC: THSPRO
   CO Area:6000

   copy from
   PC:11100101
   CO Area:600
   ```



   Assign company code and click save
   - creation of cost center(ks01)

   ```
   example:

   CO Area:6000
   CC: THSCOS
   Valid from: 01.01.2019 to 31.12.9999

   reference

   CC: 40012001
   CO: 6000

   ```

   Accounting -> joint venture accounting
- change company code and profit center and click save option

#### MM 
  - Define the Plant code and change name of plant code 
   ```
   Enterprise Structure -> Definition -> Logistics General -> copy,delete and check plant 

   example:

   copy plant: 4111
   to plant : THSC 

    Change name of Plant
   ```

  - Define Storage location
  ```
   Enterprise Structure → Definition → Materials Management → Maintain Storage Location
  ```
  - Define Purchasing Organisation
    ```
     Enterprise Structure → Definition → Materials Management → Maintain Purchasing Organization
    ```
  - Assign the Plant to the Company Code 
   ```
    Enterprise Structure → Assignment → Logistics General → Assign plant to company code
   ```
  - Assign the Purchase Organization to the Plant
    ```
    Enterprise Structure → Assignment → Materials Management → Assign purchasing
    organization to plant
    ```
  
#### SD 
  - Define the Sales Organization(Ref-4100)
  ```
    Enterprise Structure → Definition → Sales and Distribution → Define, copy, delete , check sales organization

   - Change name of sales orginsation
  ```

- Define the Distribution Channel
- Define the Division
- Define the Shipping Point (Required for SAP TM Integration)
- Assign Sales Organization to Company Code

  ```
  Enterprise Structure → Assignment → Sales and Distribution → Assign sales organization
  to company code

  ```

- Assign Distribution Channel to Sales Organization
- Assign Division to Sales Organization
- Set Up the Sales Area
- Cross-Module Integration: Assign Sales Organization / Distribution Channel to Plant
   

1. creation of purchase group 
   ```
   SPRO -> SAP reference img -> Materials Mangement -> Purchasing -> Create purchasing group

   click new enteries and save 
   ( THS ||  THSC Buyer group)
   (KNR || ASRC BUYER GROUP)
   (AVRC || AVRC BUYER GROUP)

   ```

2. creation of orginazational model
   to open organisational model "PPOME"

   ```
   SPRO -> SAP reference img -> Transportation Mangement -> master data -> Organisational management -> organisational Model 

   ``` 


3.  Activation of ledger plant(omx3,omx2,omx1,CKMSTART)
    - SE38 or SE32-TO decativate plant (SAPRCKMJX)
    - OMS2 to check material of FERT
4.  creation of material master(mm01)
5.  Creation of BP (customer and carrier)8999999492
   - Customer - 0300004187
   - BP (00000)-> Customer(FLCU00) ->customer (FLCU01) 
   - carrier - 0300004189
   - BP(00000) -> Supplier(FLVN00) -> Supplier(FVLVN01) -> Carrier(CRM010)
   OVKK= SPRO → Sales and Distribution → Basic Functions → Pricing → Pricing Control → Define and Assign Pricing Procedures
6. Define LIP
    - Control keys (SPRO -> SAP ref IMG -> TM -> INTEGRATION ->LOGISTICS INTEGRATION -> INTERNAL TM)
    - Define LIP(under we have FUBR blank )
    - Define Transportation relevance of sales Document (edit seen enteries)
    - Create fubr in fiori screen 
    - UPDATE in LIP  (FUBR)


7.  Creation of sales area(VA01)(110089)
8.  creation of frieght Unit type
    - SPRO -> SAP img REF -> Transportation Mangement -> Planning -> Frieght unit -> define frieght unit types
    - after creation with ref-0001 and go to firori screen and open edit fubr.
    - enter "AVRC" in document type and save
    - create another sales area(VA01) (110120) (112757)(114278) (114559)
  
9.   creation of freight Order type 
    - SPRO → SAP Reference IMG → Transportation Management → Freight Order Management → Freight Order → Define Freight Order Types
    - create with ref:1000 and name it "AVRO"
    - open firori screen  and enter "AVRO" in Document type and save
    - creation of sales area(VA01) ( 110902) 

10. Define Means of transport 
    - (TM-> master data -> resouces -> Means of transport and compartment -> Define means of tarnsport)
  
     ```
     example : TRUCK_AVRC

     ```

    - create resources (till Transportation cockpit its okay)
    - (SAP Menu -> Logistics -> TM -> Master Data -> Resource )
    
    ```
    BOX_TRUCK_AVRC 
    FLATBED_TRUCK_AVRC
    TANK_TRUCK_AVRC 
    SMALL_TRUCK_AVRC
    TINY_TRUCK_AVRC

    Enter location and means of transport contionous dim,factory calender,capacity,unit

    ```

        - define transportation lanes(/n/SCMTMS/TL5)(connecting means of transport to carrier)
        - define transportation zones(/n/SCMTMS/ZONE)(AV_ZONE1,AV_ZONE2)(defining souce and destination loactions as zones)
    - WE are extracting source location(SP_AVRC) and destination loaction(0300004187 - Cutomer) by displaying frieght unit type

###  (Transportation Cockpit)
   1.  Create selection profile 
    - selection profile (FU_SP_AVRC) (Frieght unit selection profile AVRC)
    - time related selected attributs (TRSA_AVRC)
    - geographical selection attributes (GSA_AVRC)
       we add our source and destination location
    - additional selection attributes (ASA_AVRC)
       we add Freight unit and freight order for business object selection 
   2. Planning Profile
      - Planning profile(PLAN_PRO_AVRC)(Planning Profile AVRC)(ref:Default)
      - CDCS update define per category and add freight order 
      - CASS  update strategy as  "Use Transport lane settings"
      - CSS give vehicle resources here 
 
   3. pagelayout for TC (used pre defined) 
   4. GO TO PLS for transportation cockpit (Profile and settings)  
   5. assign for users 
   6. go to planning -> transportation cockpit (AVRCO_PLS)(TCS_AVRC)

### TCM(Transportation Charge Management)
- We are following Bottom -Up Approach
- Frieght Settlement Document(Calculation in Frieght order / Frieght booking )
- Goto Charge management
11. Create scale
    - AV_LOC(AVRC source location) as LOC RS_LOC
    - AA_LOC(AVRC Destination location) as LOC RD_LOC
    - AV_GROSSWeight (AVRC Gross weight) as Weight RD_GROSSWEIGHT
12. create rate table Definition
    - Define rate table types
      SPRO -> sap img ref -> TM -> Master data -> Rate Tables -> Define Rate table type 
      (AVRC)
      
    - Define Charge Types 
       SPRO -> sap img ref -> TM -> Basic functions -> Charge calculation -> basic settings -> Define charge Types 
       A2CC_BASE_CHAR= AVRC_BASEFRT (BASIC CHARGES)  
       YT_HA_FUEL = AVRC_FUEL (FUEL CHARGES)
       YT_HA_STOP = AVRC_BNR (BUNKER CHARGES)

    - create rate table definition(Friori screen) 55 mins  
       RT_AVRC =BASIC CHARGES
       RT_AVRC1 = FUEL CHARGES
       RT_AVRC2 = BUNKER CHARGES 
       . General Data -> insert scales 
       . Update charge type for every rate table 

    

13. Charge calucation sheet - create calculation sheet 
    - AVRC_TCCS
  
14. Frieght agreement
     SPRO -> sap img ref -> TM -> master data -> Agreement and service product -> define frieght Agreement Types 
     (AVRC - Frieght agreement type)

    - Create Frieght Agreement (Contract manager) 
      (8143844186) 


### Frieght settlement Document 
#### part-1 OKB9  OCT28 
1. Create Frieght settlement Document
   SPRO -> sap img ref -> TM -> settlement -> Frieght settlement -> Define Frieght settlement Document Type (ref: ZFUS)
    - Frieght settlement Document Type (AVRC)
    - Update "FSD type"  in Frieght order type "AVRO"
 
 
    - AC03 = Create Service master
      Activity Number : 3008143,3008296 Base freight Service for AVRC

    SPRO -> Sap img ref -> TM -> Settlement -> Frieght settlement -> Integration for settlement posting -> Assign purchasing information for posting 
    - Assign purchasing information for posting (Assigning plant and purchase group here) 
    - Map transportation charge type to service master road (600,600000,AVRC_ROADFRT,3008143)
  
    - define charge type again with "AVRC_FSC" 

##### part-2 
SPRO -> sap img ref -> TM -> Settlement -> Define settlement profile (ref:ZSP_ROAD)
  - Define Settlement profile "AVRC_SETPR" 30mins 

SPRO -> SAP img ref -> TM -> Basic functions -> Cost distribution -> Define cost distribution profile (ref: A2CC_C_DIS)
   - define cost Distribution profile "AVRC_DISPR"
  
SPRO -> Sap img ref -> TM -> Basic functions -> Charge calculation -> basic settings -> Define calculation profiles (ref:A2CCCALPRO)
   - Define calculation profiles "AVRC_CALPR"

SPRO -> sap img ref -> TM -> Basic functions -> Charge calculation -> basic settings -> Define charges profile
 - Define charges profile "AVRC_CHAPRO" "RSBP_CHARPR"
    - update the settlement profile 
    - update calculation profile 
    - update cost distribution profile 
  
- update in organisational model under purchase org AVRC "AVRC_CHAPRO" 
- Go to BP under select carrier and go to PURCHASE ORG and update CALCULATION PROFILE & settlement Profile. 

####  Post frieght settlement document OCT29
 
 - goto frieght order type and click on create frieght settlement document 
 - 8100003831 - Frieght settlement document
 - MMPV posting period 



2. Accruals posted

SU3 Maintain user profile
POK X 
SCL G
TM_INVOICE CLERK

SPRO -> SAP ref img -> Integration with other SAP components -> TM -> Invoice Integration -> Mapping for cost distribution -> Assing transportation charge types to condition types


charge category charge subcategory charge type
004    101000    Basic freight
002    301008    Fuel Surcharge
002    301001    Bunker adjustment factor 

MMPV - Posting period  
MIRO - to open invoice  screen 


SPRO -> SAP ref img -> SCM Extended warehouse management -> SCM basics -> Integration -> Basic settings for creating the system landscape -> Assign local system to queue type





      

### Oecan Scenario

#### Create Locations 
- Logistics -> TM -> Master data -> Transportation network -> Location -> /SCMTMS/LOC3 
   1. Location : NYPORT3 NewyorkSea Port, Location type: Port (1100)
    -  click create and go to Address TAB
      Title: Company 
      Name : NY Port
      US,NY

   2. Loaction : AMSPORT3 AmsterdamSea Port , Location type: Port(1100)
    - click create and go to Address TAB
      Title: Company 
      Name : AMS Port
      NL, DR


- Create default route (Friori Screen)(3000861)
   SP_AVRC,NYPORT,AMSPORT,0300004187

- With existing FUBR copy and change to 
   Description: default route _AVRC_FUBR 
   FUBR: AVRC_FUBR_AR
   Click apply default route option and save 

- Go to LIP and change FUBR  



- Define Charge subcategories
  SPRO -> sap img ref -> TM -> Basic functions -> Charge calculation -> basic settings -> Define charge subcategories
  
  " 600000 - AVRC_Road Freight , 600001 - AVRC_Oecan Frieght, 600002 - AVRC_AIR Frieght"

- Define charge Categories
  SPRO -> sap img ref -> TM -> Basic functions -> Charge calculation -> basic settings -> Define charge Categories

  "600 - AVRC_BASE Frieght" 

  IMP- give the charge category under all subcategory

- Define Charge Type 
SPRO -> sap img ref -> TM -> Basic functions -> Charge calculation -> basic settings -> Define charge Type
(AVRC_RoadFRT)




   





### IMPORTANT 
- Capacity selection settings the means of tarnsport and resources are added.
- In carrier selection settings change strategy to "use transportant lane settings"
 


### Assigning shipping point 

-  Enterprise Structure -> Definition -> Logistics Exceution -> Copy ,Delete and Check Shipping Plant 

```
example :
From shipping point:4111
to shipping point: THSC

```

-  Enterprise Structure → Definition → Logistics Execution → Define shipping point 
    (change name of shipping point) 

- Enterprise Structure -> Assignment -> Logistics Exceution -> Assign shipping point to plant 
   
   OR 

- SPRO -> SAP refernece img -> Logistics Execution → Shipping → Basic Shipping Functions →   Shipping Points and Goods Receiving Point Determination → Assign Shipping Point 
( Shipping Point Determination Backend Logic)


TVSTP: Assign Shipping Points to Plant
TVKWZ: Assign Sales Organization-Distribution Channel-Plant
TVAK: Sales Document Types
TVAKT: Language Specific descriptions for Sales Document Types
TVCPA: Copying Control: Sales Documents

TVSWZ


Block profile

spro -> sap img ref -> TM -> Frieght order management -> Define Block profile


Assign shipping point to plant 
Assign Distribution channel to plant 



### synchronously process
1. Open transaction SE38.
2. Enter /SCMTMS/SFIR_TRANSFER_BATCH.
3. Click Execute (F8).
4. Enter the FSD number.
5. Enter the relevant FSD Type, Purchasing Organization and Purchasing Group.
6. Select the appropriate lifecycle status for eligible documents.
7. First run in Simulation Mode to check which documents are selected.
8. If the document is eligible, run the report without Simulation Mode.
9. Check the FSD Application Log and refresh its status.



### manual  tendering
1. Create freight order and goto subcontracting tab 
2. In Tendering overview click new option and goto below 
3. insert carrier and save (RFQ is generated)
4. select RFQ and click Publish and save 
5. goto tendering worklist and goto RFQ and create quotation 
6. Click submit quotation and save
7. open se38 and /SCMTMS/TEND_CONT_PROCESS  and enter purchasing org 
8. click award quoatation and send FO and select "set to confirmed by carrier"

 

MIGO
OKB9 
490014332 POSTED 
mmbe 

 4500077376 purchase order

4500077376


  

/SAPAPO/CREATE_LOCATION
/SCMTMS/BUPA_FOR_LOCATION 
SBGRFCMON

TM_BGRFC_INBOUND



CC - 4001
PLANT 4111
SALES ORG 4100

