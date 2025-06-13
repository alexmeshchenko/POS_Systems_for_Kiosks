# iPad POS Systems for Kiosks in Sweden

iPad POS integration (tablet + card reader + software) can serve as a full-fledged alternative to external terminals like PAX IM30 in Swedish self-service restaurants. This approach combines order interface and payment processing in a single device, simplifying infrastructure. However, for success, it's important to consider regulatory requirements (fiscalization) and the necessity of payment providers. Below are the key issues, leading solutions (Lightspeed, PayPal Zettle, SumUp, and others), their comparison, and selection recommendations.

## iPad POS vs External Payment Terminals

### iPad POS Capabilities
Modern POS applications turn an iPad into a full-featured cash register and payment terminal. For example, Zettle (formerly iZettle) offers a certified cloud-based cash register solution that works simply as an application on a tablet or smartphone. This means that instead of a separate terminal and cash register, an iPad with software and a connected card reader is sufficient to accept cards, print receipts, and register sales. This solution saves space and doesn't require expensive equipment – there's no "black box" (control unit) since fiscal functions are implemented in the cloud. Thus, with proper implementation, iPad POS can completely replace a specialized terminal like PAX IM30.

### Comparison with PAX IM30
Terminals like PAX IM30 are autonomous devices initially certified for payments (EMV, PIN codes) and often used in cashier-less kiosks. They have built-in protection (PCI), receipt printer, and can operate without being connected to a tablet. An iPad is a universal device requiring an external card reader (e.g., via Bluetooth or connector) and appropriate software.

**iPad approach advantages**: flexible custom order interface, larger screen, unified platform for UX and payment, easy app updates.

**Disadvantages**: iPad itself is not certified for reading bank cards – requires connection of a certified reader; also, the tablet is less adapted to harsh conditions (moisture, vandalism), so it needs protection with a housing in kiosks.

### Practice and Benefits
Large food service chains have demonstrated the effectiveness of self-service kiosks. For example, kiosk implementation increased average check by ~20-30% due to upselling and order convenience. Users readily switch to self-service if the interface is intuitive and there are no queues. An iPad with a touch application provides such an experience, similar to professional kiosks, but at lower cost and greater development flexibility.

### Regulatory Aspects
In Sweden, any POS accepting cash or cards must be connected to a certified cash register (control unit) if annual turnover exceeds ~229,200 SEK (4 basic amounts). Traditionally, this is a physical "black box" (kontrollenhet) for each cash register. iPad-based solutions can meet these requirements either through cloud fiscal services (like Zettle) or with the help of an external certified device. For example, Zettle Go is included in Sweden's approved cash register systems registry and automatically maintains fiscal records online. Thus, iPad POS using certified software is completely legal and registers with Skatteverket as a cash register. It's important to ensure that the chosen solution (software) is in Skatteverket's list – otherwise, integration with an external control module will be required.

## Role of Payment Providers and Acquirers

Using iPad + card reader does not eliminate the need for a payment provider or acquirer. Any card acceptance involves a participant licensed for transaction processing. In the case of iPad POS, PayFac (Payment Facilitator) aggregators like Zettle, SumUp are usually used, which handle acquiring themselves. For businesses, this is simplified: no separate contract with an acquiring bank is needed – just an account with a service (Zettle, SumUp, etc.) that charges commission for transactions. Unlike classic solutions (Bambora, Nets), which require monthly terminal subscription and separate internet acquiring with commission, aggregators usually have no fixed fee, and commission (e.g., ~1.75-1.85% per payment) already includes acquirer services.

### When choosing an iPad POS approach:

• **If using a ready-made solution** (Zettle, SumUp, etc.), the acquirer is "hidden" within it – these companies are themselves payment institutions (e.g., SumUp is authorized as an electronic money issuer in the EU). Nevertheless, the business connects to their service, essentially entering into an offer agreement for acquiring services. Thus, a payment provider is still needed, just integrated into the software.

• **If making a custom integration**: you'll need to use APIs from banks or providers (Adyen, Stripe, etc.), which again involves agreements with them. Direct work with international payment systems is impossible without an acquiring bank. In the end, iPad POS requires either connection to a PSP/acquirer or use of an aggregator SDK.

**Practical example**: Lightspeed POS in Sweden allows integration of external payment gateway Zettle for card acceptance. That is, even a large POS platform relies on a local provider for payment processing.

**Summary**: the iPad and application themselves cannot accept cards without a third-party service. Either a built-in solution (Zettle, SumUp) or integration with an acquirer is needed.

**Conclusion**: The iPad POS paradigm simplifies interface and management but doesn't eliminate payment infrastructure – it just becomes software-oriented. Business still requires a contract with a provider (even if just a few clicks through an application) for payment processing and fund settlement.

## Key iPad POS Solutions for Sweden

Let's examine the main iPad-based POS platforms relevant in the market, their compatibility with custom applications, and supported functions. Below is a comparative table by criteria important for Swedish self-service:

• **Swish**: support for popular mobile payment Swish (via QR or integration).
• **Fiscal compliance**: availability of certified cash register mode for Skatteverket requirements.
• **SDK/API (custom integration)**: ability to embed payments/functions in proprietary kiosk application.
• **Peripherals**: supported external devices – receipt printer, scanner, proprietary card readers, etc.
• **Features**: notes – offline mode, payment model, limitations, and strengths.

## Comparison of Popular iPad POS Platforms (Sweden)

| **Solution** | **Swish** | **Fiscal Mode** | **Integration (SDK/API)** | **Device Support** | **Features and Notes** |
|-------------|-----------|-----------------|---------------------------|-------------------|----------------------|
| **Lightspeed POS** | Not directly (through third-party integrations)<br>*(can use Swish via Zettle or Adyen)* | Yes, when connecting certified block or cloud service<br>*(Lightspeed itself works in Sweden with cloud control through partners)* | **REST API**, open platform;<br>250+ integrations; no direct SDK for payment reader (relies on external gateways) | Printers (Ethernet, Bluetooth);<br>Card readers and terminals (Verifone, Zettle, etc. through integration);<br>Barcode scanners, customer displays | **Advanced POS system** (product management, inventory, analytics). Has **offline mode** (sales without internet). Available in 100+ countries. Lightspeed Payments commission ~2.6%+€0.10 (or use external providers). Suitable for medium and large businesses, chains. |
| **PayPal Zettle** | **Yes**, through QR codes in app<br>(payment goes directly to Swish account, sale registration in Zettle) | **Yes**, cloud cash register software; certified by Skatteverket. Control module – **in cloud** (no "black box") | **SDK for iOS/Android**, API for products/reports. Has **client SDK** for payment acceptance in third-party application. | Branded card readers (Bluetooth) and Zettle terminals; Receipt printers (compatible Star, Epson models); Cash drawer, scanner – through compatible devices. | **Local leader**: founded in Sweden, focused on small and medium business. No subscription for POS app, commission ~1.85%. For fiscal mode Zettle Go Plus ~299 SEK/month. Simple setup: iPad + reader. **Limitations**: relatively simple functionality (basic product management), limited interface customization. But **best local compliance** and Swish availability. |
| **SumUp** | No built-in<br>(can accept separately through bank and mark as external payment) | Not completely – SumUp app is not a cash register<br>(separate solution needed for fiscalization). Small business below turnover threshold can operate without cash register. | **Wide SDK/API:** iOS, Android SDK for card readers; API for online payments. Easy to embed payment in your application (SumUp processes transaction). | Branded SumUp Air/Pro card readers (Bluetooth, 3G); Printers: limited (no proprietary, but can print receipts via AirPrint or send SMS/e-mail). | **European fintech**: very simple connection, no subscription, commission ~1.75%. Features **advanced SDK** – convenient for custom solutions (kiosks). **Minus for Sweden**: doesn't solve fiscal task by itself – SumUp advises entrepreneurs to use local cash register system in parallel. Suitable if custom kiosk needed: SumUp SDK integrates into app, fiscal accounting can be implemented through partners (e.g., Efsta EFR). |
| **Square** | No (Square doesn't work with Swish) | **No** – **card processing not supported in Sweden**. Square POS app available, but **can't accept cards** (only cash or external methods). | Has SDK (Reader SDK, Terminal API) and excellent technical capabilities, but **not applicable in Sweden for cards**. | Officially Square equipment not sold in Sweden; its use not certified and not supported. | Square – major player (USA, Europe), but **not yet launched in Sweden** for acquiring. Not suitable for kiosk since won't allow accepting local payments. *(App can be used for cash accounting, but that's a partial scenario.)* |
| **Shopify POS** | No direct<br>(supports only Klarna for online, no Swish) | Partially: Shopify POS app works in Sweden, **but** Shopify Payments (acquiring) for offline **not available**. Need to connect compatible terminal (e.g., Zettle) and maintain fiscal records separately. | Has API and **App Bridge** for app integration, but limited customization of payment process. | Supports printers, readers (in regions where Shopify Payments works – in Sweden need external, e.g., Zettle through integration). | Offering oriented to stores combining online and offline. **Limitation**: no native acquiring in Sweden, so for cards must use another solution (Shopify POS can work with Zettle terminal, SumUp, etc. through integrations). Suitable for those already using Shopify (e-commerce) and needing basic offline POS. |
| **Sitoo** (Swedish SaaS) | Planned through integrations<br>(mainly cards and invoice) | Yes, solution certified in Sweden<br>(cloud control). | Open API for integrations<br>(Sitoo — headless POS, can connect e-commerce, etc.) | iPad and Android apps; support for local equipment<br>(printers, scanners, Nets/Verifone terminals, etc.). | **Local player** (Stockholm). Specializes in retail, has major clients. Features good offline mode and scalability (unified cloud base for stores). In kiosk context may require customization for self-service UI. |
| **Trivec** (EU) | No (focus on cards) | Yes, through physical control block (Blackbox) in each establishment. | API limited<br>(internal system). Custom apps not main scenario. | Proprietary terminals and fiscal printers, integration with banking terminals<br>(Verifone, etc.). | **Restaurant solution** (POS+credit terminals). Reliably covers fiscal requirements, 24/7 support. But **not designed for custom kiosks** – more for complete classic restaurant software. |

**Note**: Besides those listed, there are other solutions in the market (Nets, Verifone, Yabie, Onslip, etc.), but they often offer either separate terminals or narrow specialized cash registers. Above are the most universal for the "iPad + card reader" scheme.

## Conclusions and Recommendations

1. **Full terminal replacement is possible**. The Zettle example proves that an iPad with proper software can perform all cash register and terminal functions: accept cards, Swish, and other payments, print receipts, and automatically transmit data to Skatteverket. For a restaurant kiosk, this means an external terminal (like PAX IM30) is not mandatory – a tablet in a protective housing, card reader, and connected printer are sufficient. However, you need to choose a provider whose software is certified as a cash register in Sweden, otherwise additional fiscal module implementation will be required (complicating the system).

2. **Providers and acquiring remain necessary**. Regardless of architecture, card payments require licenses and integration with the banking network. Options here are: either use an aggregator (Zettle, SumUp, etc.) or integrate a payment gateway (e.g., Adyen, Bambora). Aggregators are simpler – online registration and device ready to work, fixed commissions and no separate subscription. With custom integration, you'll need to enter an acquiring agreement and go through POS application certification under PCI DSS. **Recommended** for quick start to use services of a proven PSP instead of developing proprietary processing.

3. **Swish support desirable for customer convenience**. In Sweden, ~8.5 million Swish users, about 39% of all e-commerce operations go through it. For a fast-food or store kiosk, this is a demanded payment method (customer scans QR and pays from smartphone). **Best solution**: use existing mechanisms – e.g., Zettle Go generates QR code and accounts for payment as Swish. If choosing another POS provider, ask about Swish integration possibilities: some Verifone terminals can display Swish QR on screen, or you can display static QR of linked number and manual amount entry. **Important**: as Skatteverket clarifies, Swish payment equals card payment in accounting requirements, meaning it must also be registered in the cash register. Therefore, ensure the POS application allows recording payment type "Swish" (even if money goes directly to company account).

4. **Solution comparison by applicability**:

   • **Lightspeed POS**: Suitable for large restaurants or chains wanting a comprehensive system – with menu management, inventory, analytics. Has offline mode, many integrations (e.g., delivery aggregators, loyalty programs). Kiosk variant implemented either with built-in modules (Lightspeed has self-service module) or through API and external application. Fiscally – solved through cloud (partner solutions). **Disadvantages**: high ownership cost (subscription + payment commission), complexity for small projects.

   • **PayPal Zettle**: Best choice for small and medium restaurants valuing simplicity. iPad + Zettle Reader allow quickly deploying kiosk with minimal development – just launch Zettle Go Kiosk (or use Kiosk Pro with Zettle SDK call for payment). **Pros**: full compliance with Swedish norms out of box, no monthly fee (besides cash register option). Swish, cards, Apple/Google Pay – all accepted. **Disadvantages**: limited UI customization – Zettle app has fixed functionality. But if main task is payment and receipt printing, this is sufficient.

   • **SumUp**: Recommended if planning proprietary kiosk application with unique UI/logic. SumUp provides tools to embed card acceptance into any iOS application in a couple of days. This way, user will interact with your custom order interface, and during payment – SDK connects with reader in background and processes transaction. This gives maximum flexibility (design completely on your side). **Limitations**: need to separately solve fiscalization task – SumUp app can be completely unused, but then need to maintain sales records in other software. Possible variant: your kiosk app sends sale data via API to cloud fiscal service (e.g., Efsta EFR or Infrasec) registered as cash register with Skatteverket. Such architectural approach is more complex but achievable.

   • **Others**: Solutions like Square and Clover are not suitable yet – they don't support local acquiring despite technical capability. Shopify POS can be a choice if you already use Shopify for online sales and want to unify catalogs and marketing; but prepare to connect third-party terminal for card acceptance. Local systems (Sitoo, Trivec) will ensure full legal compliance and local support, but integration with custom kiosks may be limited (they're more "closed" systems). Worth considering if priority is reliability of traditional software, not customization.

5. **Kiosk implementation recommendations**: If you're planning a restaurant self-service kiosk, including in Sweden, you can outline two paths:

   • **Minimally complex**: use Zettle Terminal or iPad + Zettle bundle, deploying in kiosk mode. This will provide a proven solution with minimal development. For Swish – activate QR in Zettle Go. All sales reports and fiscal functions will be handled by Zettle (data export available, accounting integration). Such kiosk can be quickly installed and scaled to multiple locations.

   • **Custom**: develop your application (or web page in kiosk browser) for ordering, integrate SumUp SDK (or similar SDK from another provider) for card payments. In parallel, connect cloud control unit – e.g., through API of service like Efsta that will assign fiscal IDs to receipts and store journal. Swish payments can be implemented by displaying dynamic QR with amount on screen (through Swish API from bank) and waiting for confirmation. This path gives complete UX/UI freedom (branding, order logic like McDonald's) but requires more development and testing for compliance (e.g., need to ensure receipt – electronic or paper – contains all fields per Skatteverket standard).

6. **Security and operation**: Remember that iPad kiosk is publicly accessible device. Need to enable Guided Access or Single App Mode so customers don't exit kiosk application. Use robust anti-vandal housing with floor or stand mounting. Card reader (e.g., SumUp Air) should also be secured or integrated into housing, or use terminal like Zettle Terminal (monoblock with screen and printer) for increased reliability. Regularly update software and iOS, but test updates before deployment to avoid downtime.

In conclusion, iPad platform combined with modern fintech services can provide convenient and legal self-service kiosk in restaurant. For Sweden, it's optimal to choose solution considering business scale: small ones – lean toward Zettle (simplicity), growing and demanding – Lightspeed (functionality), developers – SumUp/Adyen SDK (flexibility). Must ensure final configuration is registered with Skatteverket and each payment is properly recorded. With these conditions met, iPad kiosk will work effectively, satisfying both customers with fast service and business with revenue growth and rule compliance.

## Sources and References:

• Skatteverket – cash register requirements and mandatory fiscalization threshold
https://www.skatteverket.se/omoss/pressochmedia/debattartiklarochkommentarer/2024/2024/skatteverketsreplikkassaregisterharingetmedkontanthanteringenattgora.5.262c54c219391f2e963227c.html#:~:text=Det%20finns%20undantag%20fr%C3%A5n%20kravet,riktar%20sig%20mot%20mindre%20verksamheter

https://trivec.zendesk.com/hc/en-gb/articles/14179901946001-Swedish-fiscal-requirements-control-box#:~:text=What%20is%20it%3F


• PPRO Report – Swish statistics (8.5 million users, 39% transactions)  https://www.ppro.com/payment-methods/swish/#:~:text=Image

• PayPal Zettle (iZettle) – cloud cash register solution and Swish support
https://www.zettle.com/se/kassasystem/kassaregister#:~:text=Ett%20kassaregister%20syftar%20p%C3%A5%20en,bara%20en%20mobil%20eller%20surfplatta

https://www.zettle.com/se/betallosningar/swish#:~:text=Swish%20och%20Zettle%20funkar%20tillsammans,i%20din%20Zettle%20Go%20app

• Expertvalet (iZettle, SumUp, Swish comparison) – payment model and acquiring features
https://www.expertvalet.se/blogg/2018/05/alternativ-till-izettle#:~:text=Maestro%2C%20American%20Express%20N%2Fa%20Mobile,kod%20kan%20anv%C3%A4ndas%20p%C3%A5%20fakturor

https://www.expertvalet.se/blogg/2018/05/alternativ-till-izettle#:~:text=Den%20st%C3%B6rsta%20skillnaden%20p%C3%A5%20kortl%C3%A4sare,maskin%C2%A0tillsammans%20med%20ett%C2%A0inl%C3%B6senavtal%C2%A0som%20innefattar%20transaktionsavgiften

• SumUp Developers – SDK/API documentation for payment integration
https://developer.sumup.com/#:~:text=Quick%20integrations

• Lightspeed & iZettle – payment integration in Sweden
https://resto-support.lightspeedhq.com/hc/en-us/articles/226405728-Setting-up-the-iZettle-terminal#:~:text=support,Germany%2C%20France%2C%20Spain%2C%20Netherlands%2C

• PYMNTS / HBR – kiosk effect on average check (+30%)
https://www.wavetec.com/blog/mcdonalds-leveraging-self-service-technologies/#:~:text=Image%3A%20long%20queue%20outside%20restaurant

https://www.pymnts.com/news/retail/2018/self-service-kiosks-qsrs-consumer-spending/#:~:text=The%20increase%20in%20consumer%20spending,79

• Square Support – country list (Scandinavia support absence)
https://squareup.com/help/ca/en/article/4956-international-availability#:~:text=Card%20payment%20acceptance%20with%20the,com%2Fnews
