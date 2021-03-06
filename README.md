**Service Document for Aykargo Shipment Transactions**

Service runs through the test link at <https://api.aykargo.com.tr>.  Account details for the test



Service descriptions consisting of 3 methods in total are as follows.

**SETDELIVERY** : Allows to create shipment

**CANCELDELIVERY :** Allows to cancel shipment

**TRACKDELIVERY :** Allows to track shipment

In general, services are triggered as TOKEN. Successful transactions will return 200, whereas failed transactions will return 500

***TOKEN Transaction***

TOKEN can be received by sending **client**, **password** fields.** 

***SETDELIVERY Method***

**Shipment Creation Method**

You can trigger shipment in 4 different ways

Type 1 : Your Location >> Your Client

Type 2 : Your Client >> Your Location

Type 3 : Your Supplier etc. >> Your Client 

Type 4 : Re-shipment order

Type 5 : Point of Delivery 

Type 6 : Point of Return

You can create shipment between all units you work with. You can also receive service as delivery and return point.

You can forward the shipment to the target branch with CityID and DistrictID from City and District details which will be provided to you in advance. 

Using the Ids provided to you as ID, you can target the branch info which you want to use for delivery and return point.

SETDELIVERY is the method that allows you to create shipment. BOLD fields are mandatory.

**DeliveryType** : It covers Type 1 ,2 ,3, 4,5,6 options given above. It indicates the point of collection and point of delivery of the shipment. It is the variable for which integer should be sent.

ReferenceNo : It covers the reference number which you use internally. It receives string value. Using this value, you can track your shipments and create return requests.

Description : You can use this field if you wish to enter any special information or description about the shipment. A string value may be entered. 

*NOTE :* 

*deliveryType : In case of 1, Sender block will not be filled. **Receiver field is mandatory***

*deliveryType : In case of 2, Receiver block will not be filled. **Sender field is mandatory***

*deliveryType : In case of 3, **Sender Receiver blocks are mandatory***

*deliveryType : In case of 4, **ReferenceNo is a mandatory field.** There is no need to send Sender and Receiver blocks.*

*deliveryType: In case of 5, **ReceiverBranchCode is a mandatory field**.*

*deliveryType: In case of 6, **SenderBranchCode is a mandatory field**.*

**Sender** : It covers sender client's title.

SenderId : It covers sender client's special code. You can enter the client code which you use internally. (Address ID etc. may also be entered)

SenderAuthority : It indicates sender client's official.

**SenderBranchCode :** This is the mandatory field which must be sent in the return point operation. DeliveryTypeId = If 6 is not selected, it should be left empty.

**SenderAddress** : Sender client's address details should be entered

**SenderCityID** : The ID to come from the City table at the end of the document should be entered as sender client's city.

**SenderDistrictID :** The ID to come from the District table at the end of the document should be entered sender client's district

**SenderPhone :** It indicates sender client's phone number.

**SenderGSM :** Sender client's GSM number should be entered.

*Either of Phone or GSM fields must be sent*

SenderEmail : It covers sender client's e-mail address

**Receiver** : It covers receiver client's title.

Receiver Id : It covers receiver client's special code. You can enter the client code which you use internally.

**ReceiverBranchCode :** This is the mandatory field which must be sent in delivery point operation. DeliveryTypeId = If 5 is not selected, it should be left empty.

receiverAuthority : It indicates receiver client's official.

**ReceiverAddress** : Receiver client's address details should be entered

**Receiver** **CityID** : The ID to come from the City table at the end of the document should be entered as receiver client's city.

**receiver** **DistrictID :** The ID to come from the District table at the end of the document should be entered receiver client's district

**Receiver** **Phone :** It indicates receiver client's phone number.

**Receiver** **GSM :** Receiver client's GSM number should be entered.

*Either of Phone or GSM fields must be sent*

ReceiverEmail : It covers receiver client's e-mail address

**PaymentType** : As a standard, 1 should be entered into this field.

**CollectionType :** It shows the payment type for cargos with collection

`	`0 ??? Indicates that there is no cargo with collection

`	`1 ??? Cash

`	`2 ??? Credit card 

` `Value 0 ,1 or 2 should be sent.

CollectionPrice : It shows how much you will collect from your client for cargos with collection. The amount to be collected should be sent. If CollectionType value is 0, CollectionPrice should be 0.

DispatchNoteNumber : It covers the dispatch serial and number which you created for your client. If entry is available, you can query your shipments.

ServiceType : It indicates the service type. Default 1 should be sent excluding special operations.

BarcodeLabelType : It indicates the printing type for the barcode label which you will get at the service return.

`	`0 = Base64 ve ZPL	1 = Base64	2 = ZPLProducts : The detail of the shipment info received as array. While you can send this as total count, you can also send in different ways by detailing your shipments.

**Count :** It indicates the count/quantity of shipments. Count/quantity should be entered for each detail. Barcode number will be generated as many as the count total.

ProductCode : It covers the code (Stock code etc.) used on your side for the product you send.

Description : You can enter description about the product. You can use it as product name 

Deci **:** You can enter the shipment deci details of the product. If you did not enter, measurements are completed by us.** 









***After you POST this method, this will return you the TAK??PNO (trackingNo), TAK??PNO URL (TrackingNo Url, BASE64 BARKOD (base64 barcode) and/Or ZPL Zebra Barcode (ZPL Barcode) code. Successful transactions will return 200, whereas failed transactions will return 500 header info. Other than that, error codes for the missing fields are as follows.***

("Delivery Reference No Cannot be Null."), 102)

("Wrong Delivery Type"), 103)

("Products Cannot Be Null"), 104)

("Payment Type Is Not Correct."), 411)

("Collection Type Not Found"), 105)

("Product Price Cannot Be Zero."), 410)

("Receiver Cannot Be Null"), 201)

("Please Enter Receiver Phone or GSM Number"), 207)

("Receiver Address Cannot Be Null"), 202)

("Receiver District Id Cannot Be Zero."), 203)

("Receiver City Id Cannot Be Zero."), 204)

("Receiver City Id is Not Correct."), 205)

("Receiver District Id is Not Correct."), 206)

("Sender Cannot Be Null."), 301)

("Please Enter Sender Phone or GSM Number"), 307)

("Sender Address Cannot Be Null."), 302)

("Sender District Id Cannot Be Zero."), 303)

("Sender City Id Cannot Be Zero."), 304)

("Sender City Id is Not Correct."), 305)

("Sender District Id is Not Correct."), 306)

("Sender Cannot Be Null."), 301)

("Please Enter Receiver Phone or GSM Number"), 207)

("Please Enter Sender Phone or GSM Number"), 307)

("Sender Address Cannot Be Null."), 302)

("Sender District Id Cannot Be Zero."), 303)

("Sender City Id Cannot Be Zero."), 304)

("Sender City Id is Not Correct."), 305)

("Sender District Id is Not Correct."), 306)

("Receiver Cannot Be Null."), 201)

("Receiver Address Cannot Be Null."), 202)

("Receiver District Id Cannot Be Zero."), 203)

("Receiver City Id Cannot Be Zero."), 204)

("Receiver City Id is Not Correct."), 205)

("Receiver District Id is Not Correct."), 206)

("Product Count Cannot Be Zero."), 401)


***CANCELDELIVERY Method***

You can cancel the shipment using the TrackingNo or your ReferenceNo fields which you entered. You can ensure cancellation for products not received by ADG. If the shipment is received, no cancellation can be done.

Error codes for the missing fields are as follows.

("Please Enter Tracking Number or Reference Number."), 701)

("No Delivery Found."), 702)

("You Cannot Cancel , Delivery Has Already Sent."), 703)





***TRACKDELIVERY Method***

It will return details of your shipment. You can track the shipment using the TrackingNo or your ReferenceNo fields which you entered.







*The status codes which you can track through specific statuses are as follows.*

*101		Cargo Shipping Order Received*

*102		Document Issued*

*103		Branch TM Loading*

*104		TM Branch Unloading*

*105		TM Line Loading*

*106		TM Line Unloading*

*107		TM Branch Loading*

*108		Branch TM Loading*

*109		Branch Distribution Loading*

*110		Branch Distribution Unloading*

*111		Delivered*

*112		Receiver Phone Incorrect*

*113		Return Request*

*114		Receiver Absent at the Address*

*115		Receiver Address Incorrect*

*116		Order Error*

*117		Damaged Shipment*

*118		Lost Cargo*

*119		Transfer*

*120		Incomplete Delivery*

*121		Out of Distribution Area*

*122		Payment Type Rejected*

*123		Delivery on Appointment*

*124		Mobile Distribution Region*

*125		Missing Cargo*

*126		Routing*

*127		Line Vehicle Delay*

*128		Line Vehicle Delayed from Transfer*

*129		Carriage Cost Found Expensive*

*130		Not Delivered*

*131		Returned Shipment*


***ANNEXES***

*City ID*

|ID|city|
| :-: | :-: |
|1|ADANA|
|2|ADIYAMAN|
|3|AFYON|
|4|A??RI|
|5|AMASYA|
|6|ANKARA|
|7|ANTALYA|
|8|ARTV??N|
|9|AYDIN|
|10|BALIKES??R|
|11|B??LEC??K|
|12|B??NG??L|
|13|B??TL??S|
|14|BOLU|
|15|BURDUR|
|16|BURSA|
|17|??ANAKKALE|
|18|??ANKIRI|
|19|??ORUM|
|20|DEN??ZL??|
|21|D??YARBAKIR|
|22|ED??RNE|
|23|ELAZI??|
|24|ERZ??NCAN|
|25|ERZURUM|
|26|ESK????EH??R|
|27|GAZ??ANTEP|
|28|G??RESUN|
|29|G??M????HANE|
|30|HAKKAR??|
|31|HATAY|
|32|ISPARTA|
|33|MERS??N|
|34|??STANBUL|
|35|??ZM??R|
|36|KARS|
|37|KASTAMONU|
|38|KAYSER??|
|39|KIRKLAREL??|
|40|KIR??EH??R|
|41|KOCAEL??|
|42|KONYA|
|43|K??TAHYA|
|44|MALATYA|
|45|MAN??SA|
|46|KAHRAMANMARA??|
|47|MARD??N|
|48|MU??LA|
|49|MU??|
|50|NEV??EH??R|
|51|N????DE|
|52|ORDU|
|53|R??ZE|
|54|SAKARYA|
|55|SAMSUN|
|56|S????RT|
|57|S??NOP|
|58|S??VAS|
|59|TEK??RDA??|
|60|TOKAT|
|61|TRABZON|
|62|TUNCEL??|
|63|??ANLIURFA|
|64|U??AK|
|65|VAN|
|66|YOZGAT|
|67|ZONGULDAK|
|68|AKSARAY|
|69|BAYBURT|
|70|KARAMAN|
|71|KIRIKKALE|
|72|BATMAN|
|73|??IRNAK|
|74|BARTIN|
|75|ARDAHAN|
|76|I??DIR|
|77|YALOVA|
|78|KARAB??K|
|79|K??L??S|
|80|OSMAN??YE|
|81|D??ZCE|

*DISTIRCT ID*

*ID	district*

*82228	ADALAR*

*82230	ARNAVUTK??Y*

*33194	ATA??EH??R*

*33221	AVCILAR*

*33308	BAH??EL??EVLER*

*33356	BAKIRK??Y*

*33406	BAYRAMPA??A*

*33268	BA??CILAR*

*33375	BA??AK??EH??R*

*93737	BEYKOZ*

*33594	BEYL??KD??Z??*

*34951	BEYO??LU*

*33461	BE????KTA??*

*93736	B??Y??K??EKMECE*

*33818	EM??N??N??*

*33854	ESENLER*

*33909	ESENYURT*

*33976	EY??P*

*34138	FAT??H*

*34178	GAZ??OSMANPA??A*

*34203	G??NG??REN*

*34288	KADIK??Y*

*34374	KARTAL*

*34949	KA??ITHANE*

*34442	K??????K??EKMECE*

*34476	MALTEPE*

*34543	PEND??K*

*34562	SANCAKTEPE*

*34919	SARIYER*

*34697	SULTANBEYL??*

*34726	SULTANGAZ??*

*82294	S??L??VR??*

*34964	TOPKAPI*

*91848	TUZLA*

*35175	YEN??KAPI*

*35220	ZEYT??NBURNU*

*82301	??ATALCA*

*82302	??EKMEK??Y*

*35080	??MRAN??YE*

*35152	??SK??DAR*

*34244	??K??TELL??*

*82406	????LE*

*34963	??????L??*

*38191	GEBZE*

*38130	??AYIROVA*

*38140	DARICA*
