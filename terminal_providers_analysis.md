# Payment Terminal Providers and Self-Service Operations: A Comprehensive Analysis

**SumUp explicitly restricts unattended operations for their regular devices while major competitors like Ingenico and Verifone fully embrace self-service deployments.** This creates a clear market divide between providers that support unattended kiosk operations and those that don't, with critical implications for businesses planning self-service payment systems.

The payment terminal industry shows a fascinating split in self-service policies. While **SumUp states their devices are "designed to follow a payment flow that doesn't allow them to operate unattended,"** they simultaneously offer dedicated kiosk solutions, revealing the complexity of regulatory and technical constraints in this space. Meanwhile, traditional POS providers like Square and Stripe Terminal maintain strict attended-only policies, while enterprise-focused companies like Ingenico and Verifone have built entire product lines around unattended operations.

## SumUp's explicit policy contradictions and restrictions

**SumUp provides the clearest documentation of self-service restrictions among consumer-focused providers.** Their developer documentation explicitly states: *"Our devices are designed to follow a payment flow that doesn't allow them to operate unattended."* This policy stems from regulatory constraints, as they explain: *"As a regulated entity, we operate under strict requirements imposed by the financial regulator, the card schemes (Visa, Mastercard and American Express) and our acquiring bank... Our license is not limitless and we cannot support every business model."*

However, **SumUp's position contains a notable contradiction.** While prohibiting unattended use of their regular card readers (Air, Solo, Plus models), they actively market SumUp Kiosk solutions specifically for self-service operations. Their marketing materials state: *"The Kiosk allows customers to browse menus, place orders and pay without cashier assistance."* This suggests their restrictions apply to standard hardware being repurposed for unattended use, rather than purpose-built kiosk solutions.

The technical limitations SumUp cites include security concerns and Bluetooth dependency. Their anti-tampering mechanisms will *"permanently disable"* devices if triggered, and their regular readers require Bluetooth connection to mobile devices within 3 meters, necessitating staff supervision to initiate transactions.

## Competitor policies reveal sharp industry divide

**The payment industry splits into two clear camps on self-service support.** Square and Stripe Terminal maintain strict attended-only policies, while Ingenico and Verifone fully embrace unattended operations.

**Square explicitly prohibits unattended operations** with detailed policy documentation. Their API specialists confirm: *"our hardware and software are not currently suitable for an unattended payment scenario, such as a vending machine or unattended kiosk."* Their terms of service state terminals must be *"within line-of-sight of employees at all times"* and their Reader SDK documentation explicitly prohibits *"Using the Reader SDK to implement payment solutions in unattended terminals or unattended kiosks."*

**Stripe Terminal takes a more nuanced approach,** supporting "semi-attended" operations where *"a customer independently interacts with the terminal, but where a representative/attendant may be available in the store or somewhere nearby if needed."* They approve scenarios like *"self service kiosk with roaming employees nearby"* and *"grocery self checkout"* but prohibit fully unattended deployments.

**Ingenico and Verifone represent the opposite extreme,** with comprehensive self-service product lines. Ingenico markets their Self/3000 series as *"perfect for high-traffic environments"* with *"IK10 / IP65 rated, suitable for intensive indoor and outdoor use."* Verifone explicitly states they provide *"self-service devices"* and *"unattended payment devices that can improve transaction security, speed and reliability for vending machines and other self-service environments."*

## Critical technical challenges in self-service payment processing

**Payment error handling becomes exponentially more complex in unattended environments** where no staff can assist customers. The research reveals significant variations in how providers handle common failure scenarios.

**Square Terminal and Stripe Terminal offer the most sophisticated error handling frameworks.** Square implements comprehensive error categories including `ReaderPairingError`, `PaymentError`, and specialized `OfflinePaymentQueue` errors, with automatic retry logic and diagnostic reporting. Stripe Terminal provides multi-layered error handling with webhook-based notifications and detailed error classification including `CardError`, `NetworkError`, and `ServerError` categories.

**PIN entry errors create particular challenges for unattended systems.** Most providers follow standard EMV protocols but documentation varies significantly. Square and Stripe Terminal offer configurable retry limits and secure error handling, while SumUp and Zettle provide limited documentation on PIN failure scenarios.

When payments fail in self-service environments, the user experience becomes critical. **Square and Stripe Terminal provide rich error messaging with visual indicators,** while Zettle displays only generic "payment declined" messages. This difference significantly impacts customer satisfaction and operational efficiency in unattended deployments.

## Internet connectivity requirements create operational risks

**Connectivity requirements represent the most critical technical consideration for kiosk deployments.** The research reveals dramatic differences in offline capabilities that directly impact operational reliability.

**Zettle presents the highest operational risk** with absolutely no offline mode. The system requires constant 3G, 4G, or WiFi connectivity and becomes completely non-functional during network outages. This creates severe business continuity risks for self-service applications.

**Square Terminal and Stripe Terminal offer robust offline capabilities** that make them suitable for kiosk deployments. Square Terminal can operate offline for up to 24 hours, processing chip, PIN, and contactless payments with automatic forwarding when connectivity returns. Stripe Terminal provides similar offline functionality with sophisticated reconciliation and webhook notifications.

**True offline mode versus "store and forward" capabilities** represent different levels of operational resilience. Square and Stripe Terminal offer genuine offline processing, while SumUp provides limited transaction storage without true offline payment processing. This distinction becomes crucial for businesses in areas with unreliable connectivity.

## Refund functionality reveals critical operational gaps

**Programmatic refund capabilities are essential for self-service systems** but support varies dramatically across providers. Common scenarios requiring automated refunds include customer input errors, technical failures where payment processes but items aren't dispensed, and compliance requirements for consumer protection.

**SumUp provides excellent refund support** with full programmatic capabilities via their REST API, supporting both full and partial refunds with immediate processing. Square Terminal offers comprehensive refund systems through their Payments API with instant processing and detailed error handling.

**Zettle represents the weakest option for self-service refunds,** requiring primarily manual intervention through the PayPal dashboard with 3-5 business day processing times. This limitation makes Zettle unsuitable for fully automated self-service scenarios where immediate refund processing is critical.

**Stripe Terminal provides the most advanced refund framework** with webhook integration, sophisticated partial refund capabilities, and comprehensive error handling for failed refunds. Their system integrates with broader dispute resolution mechanisms.

## Zettle analysis reveals significant self-service limitations

**Zettle offers moderate potential for kiosk integration but with critical limitations** that make it unsuitable for many self-service applications. Their hardware lineup includes competitively priced options with the PayPal Reader at £29 and PayPal Terminal at £149, both offering good iPad compatibility.

**The Store Kit option provides the most professional kiosk-ready solution** with integrated iPad, card reader, dock, and mounting hardware ranging from £249-699. The tablet stand rotates and tilts with countertop fixing capabilities, creating an attractive customer-facing setup.

**Zettle's iOS SDK capabilities are limited** with restricted public documentation and moderate to high integration complexity. The SDK enables custom iOS app development but requires significant technical expertise and locks merchants into the PayPal payment ecosystem.

**Critical limitations for self-service applications** include the complete lack of offline mode, limited self-service documentation, and absence of specialized kiosk support. The internet dependency creates operational risks, while the PayPal ecosystem lock-in prevents processing through alternative payment processors.

## Comprehensive provider comparison and recommendations

| Provider | Self-Service Support | iOS SDK Quality | Offline Capabilities | Refund Support | Hardware Cost (SEK) | Transaction Fees (Sweden) | Key Limitations |
|----------|---------------------|-----------------|---------------------|----------------|---------------|------------------|-----------------|
| **SumUp** | ✅ Full support (dedicated kiosk solution) | ⭐⭐ Limited (fundamental cancellation flaw) | ❌ None (requires constant internet) | ⭐⭐ Basic (no real-time cancellation, 3-month limit) | 459 - 5387 + VAT | 1.49% base<br/>or 0.95–1.99% with ~220 SEK/mo subscription | No cancellation via SDK<br/>No offline mode |
| **Zettle** | ❓ Unclear (no official policy found) | ⭐⭐⭐⭐ Excellent (cancellation support, mature SDK) | ❌ None (requires constant internet) | ⭐⭐⭐⭐⭐ 365-day window, full/partial refunds | 392 - 2011 + VAT | 1.85% flat (no monthly fee)<br/>Custom rates possible >100k SEK/mo | No offline mode<br/>Policy unclear for unattended use |
| **Square** | ❌ Prohibited (attended only) | ⭐⭐⭐⭐⭐ Outstanding (4 SDK options, full cancellation) | ⭐⭐⭐⭐⭐ 24-hour offline | ⭐⭐⭐⭐⭐ Full API support | — (not sold in Sweden) | ❌ Not available in Sweden | Strictly prohibits unattended use |
| **Stripe Terminal** | ⚠️ Semi-attended only | ⭐⭐⭐⭐⭐ Outstanding (developer-friendly, full control) | ⭐⭐⭐⭐ Good (store-and-forward, limited preview) | ⭐⭐⭐⭐⭐ Excellent (comprehensive API, voids + refunds) | 619 - 3660 (Tap to Pay +1.05 SEK) | 1.4% + 1.00 SEK (EEA)<br/>2.9% + 1.00 SEK (non-EEA)<br/>+1.05 SEK Tap to Pay | Semi-attended only<br/>Offline mode not fully public |
| **Ingenico** | ✅ Full support | ⭐⭐⭐⭐ Good | ⭐⭐⭐⭐ Enterprise-grade | ⭐⭐⭐⭐ Enterprise support | ~2100 - 6300 | Custom pricing (depends on acquirer/partner) | Expensive, needs bank/acquirer contract |
| **Verifone** | ✅ Full support | ⭐⭐ Limited | ⭐⭐⭐ Standard | ⭐⭐⭐ Basic support | ~1575 - 4200 | Custom pricing (depends on acquirer/partner) | Limited developer docs<br/>No open pricing |

\* Values + VAT mean that 25% value added tax should be added at the final calculation.

** Zettle is PayPal Sweden, and offers you the possibility to make contract bets starting from >100,000 SEK per month.

*** Stripe Terminal: If you use Tap to Pay, the fee is increased by 1.05 SEK for each authorization.


A comprehensive analysis of SumUp, Zettle, Square, and Stripe Terminal reveals significant differences in pricing, capabilities, and policies that directly impact implementation decisions for different business models.

## Transaction fees show competitive clustering with key exceptions

**SumUp leads on basic pricing** with **1.69%** for UK card reader transactions on their pay-as-you-go plan, dropping to **0.99%** for consumer cards with their £19/month Payments Plus subscription. Their digital payment products charge 2.5%, while QR codes are completely free.

**Zettle and Square match at 1.75%** for UK in-person payments with no monthly fees. Zettle's invoice payments cost 2.5% for grandfathered accounts, while Square's online payments vary from 1.4% + 25p (UK cards) to 2.5% + 25p (non-UK cards).

**Stripe Terminal charges significantly more** at **2.7% + $0.05** in the US market, though UK pricing shows **1.4% + £0.10** for European EEA cards and **2.9% + £0.10** for non-European cards. Their Tap to Pay feature adds 10¢ per authorization.

Critical gap identified: Zettle's EU and Sweden pricing remains unavailable through public channels, requiring direct contact for official rates.

## iOS SDK maturity varies dramatically across providers

**Square demonstrates the most comprehensive SDK ecosystem** with four distinct integration options: Mobile Payments SDK (2.2.3), legacy Reader SDK, In-App Payments SDK, and Point of Sale SDK. Their documentation quality rates as excellent with 24/7 partner support, though they require iOS 15/16+ for latest versions and mandate application signatures for production use.

**Stripe Terminal offers the most developer-friendly experience** with iOS 14+ compatibility, comprehensive API coverage, and active GitHub repository maintenance. Version 4.0.0 introduced breaking changes but enhanced functionality. Their delegate system and error handling provide robust integration capabilities.

**SumUp provides solid mid-tier SDK functionality** supporting iOS 14+ with CocoaPods, Carthage, and Swift Package Manager integration. Their SDK covers all major card readers and includes OAuth2.0 authentication, though integration complexity rates as moderate.

**Zettle maintains active development** with version 4.16.2 released December 2024, supporting iOS 8+ but requiring developer portal access for documentation. Their strict bundle ID matching requirements can complicate integration.

## Refund capabilities reveal significant policy differences

**Zettle offers the longest refund window** at **365 days** with both full and partial refund support through app and web interfaces. Processing takes "a few business days" with refunds restricted to the original payment card.

**Square provides comprehensive refund APIs** but **no traditional void functionality**. Their 1-year time limit allows up to 20 refunds per payment ID with real-time status tracking, though balance requirements and cross-method limitations apply.

**Stripe Terminal delivers the most sophisticated refund system** with comprehensive API support, immediate API confirmation, and 5-10 business day customer processing. They support both refunds and voids for most networks, though Interac and eftpos auto-capture prevents voiding.

**SumUp limits refunds to 3 months** from transaction date with full API support via OAuth2.0 authentication. They support both full and partial refunds but require the same payment method for multi-payment orders.

## Hardware costs reflect different positioning strategies

**Zettle leads on entry-level pricing** with £29 + VAT for the first PayPal Reader, though additional readers cost £69 + VAT. Their terminal pricing starts at £149 + VAT with pre-loaded SIM cards included.

**Square offers the most aggressive entry strategy** with free basic readers (additional units £10) and contactless readers at £49 + VAT. Their current promotion offers 25% off with code FRIDAY25 until December 3, 2025, bringing the Square Stand to £74.25 + VAT.

**SumUp positions in the middle** with Air readers at £34-44 + VAT. Their dedicated kiosk solution costs £399 + VAT plus £59/month subscription with 0.99% transaction fees.

**Stripe Terminal charges premium hardware pricing** starting at $59 for the Reader M2, scaling to $349 for the premium S700 smart reader. Their Tap to Pay solution eliminates hardware costs but adds 10¢ per authorization.

## Self-service policies create clear implementation boundaries

**Only SumUp explicitly supports unattended operations** with their dedicated kiosk solution including specific Terms of Service for self-ordering kiosks in quick-service restaurants and retail environments. Case studies include Leicester City FC and Cardiff City FC implementations.

**Square and Stripe Terminal explicitly prohibit unattended use**. Square's official policy states their "hardware and software are not currently suitable for an unattended payment scenario" and requires devices to be "within line-of-sight of employees at all times." Stripe Terminal supports only "attended or semi-attended" setups, defining semi-attended as having nearby staff support.

**Zettle's policy remains unclear** despite extensive research through official terms and conditions. No specific guidance on unattended or self-service usage was found in available documentation.

## Offline capabilities create significant operational constraints

**Square leads offline functionality** with comprehensive support across all hardware devices globally since April 2024. Their store-and-forward architecture provides 24-hour offline windows with automatic synchronization, covering nearly 90% of hardware sellers.

**Stripe Terminal offers store-and-forward offline support** but currently limited to private preview. When fully released, it will support mobile readers, smart readers, and Tap to Pay devices with automatic forwarding when connectivity restores.

**Both SumUp and Zettle lack offline payment processing entirely**, requiring constant internet connectivity for all transactions. This represents a critical limitation for businesses needing offline capabilities, with official statements confirming "You need an internet connection to use the reader."

## Implementation recommendations based on use case requirements

For **traditional attended POS systems**, all providers offer viable solutions with Square and Zettle providing the most competitive pricing at 1.75%. Square's offline capabilities and comprehensive SDK ecosystem make it particularly suitable for locations with connectivity concerns.

For **self-service or unattended applications**, **only SumUp provides compliant solutions** with their dedicated kiosk offering. Square and Stripe Terminal's explicit prohibitions eliminate them from consideration, while Zettle's unclear policies create compliance risks.

For **developer-intensive integrations**, Stripe Terminal and Square offer the most comprehensive documentation and API coverage, though Stripe's higher transaction fees may impact total cost of ownership.

The **offline requirement serves as a decisive factor**, immediately eliminating SumUp and Zettle for businesses requiring offline transaction capabilities, regardless of other advantages.

