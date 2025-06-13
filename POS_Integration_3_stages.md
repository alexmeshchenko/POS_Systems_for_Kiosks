## POS Integration Evolution: 3 Stages

### Stage 1: Traditional Terminal Integration
Traditionally, we used **Ingenico payment terminals**, integrated with our iOS apps via PayEx — a reliable solution, but quite rigid and hardware-dependent.

**Characteristics:**
- External payment terminals (Ingenico models)
- Complex integration through payment processors like PayEx
- Hardware-dependent architecture
- Reliable but inflexible

### Stage 2: Basic Terminal Functionality Analysis
Since we only need basic terminal functionality (not Smart terminals), I began analyzing which devices integrators can supply. According to documentation, **Market Pay can supply PAX IM30**.

**Complete flow of the required process:**

**Kiosk App Integration (Typical workflow after receiving receipt):**
- iPad → POS (PAX IM30) → receipt printing → send to kitchen → ready → delivery

**Final payment processing solution scheme:**
```
iPad Kiosk App 
    ↓ (Handpoint iOS SDK)
POS (PAX IM30) 
    ↓ (processing system/banking network)
Swedish banks (SEB, Nordea, etc.)
```

**Characteristics:**
- Focus on basic (non-Smart) terminals
- Direct SDK integration via Handpoint iOS SDK
- Clear workflow from order to delivery
- Integration with Swedish banking infrastructure

### Stage 3: iPad POS Systems Evolution
Explored a comparatively new solution: **"iPad POS Systems for Small Business"**. This means an external terminal (like PAX IM30) is not mandatory – a tablet in a protective housing, card reader, and connected printer are sufficient.

**My task:** Integration of payment terminal with iOS application for iPad.

**Characteristics:**
- iPad-centric architecture
- Eliminates need for external terminals
- Integrated card readers and printers
- Simplified infrastructure
- All-in-one kiosk solution

## Conclusions & Recommendations

For kiosk-based restaurants in Sweden, iPad POS systems represent the optimal evolution that simplifies architecture, improves user experience, and aligns with existing customer expectations.

- **Zettle** is the most locally integrated option with native Swish support and SDK access
- **Lightspeed** is best for advanced restaurant setups but is more complex and costly
- **SumUp** is ideal for lean setups and fast onboarding