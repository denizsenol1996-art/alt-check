# Discord Verification Website - Design Guidelines

## Design Approach

**Selected Approach:** Design System (Utility-Focused)

**Rationale:** This is a server moderation tool where trust, clarity, and security perception are paramount. The design should feel professional, aligned with Discord's ecosystem, and prioritize information comprehension over visual flair.

**Key Principles:**
- Trust-first design: Clean, professional aesthetic that reinforces security
- Discord ecosystem alignment: Visual harmony with Discord's interface
- Information clarity: Easy-to-scan consent details and verification flow
- Minimal friction: Streamlined path from landing to verification

---

## Core Design Elements

### A. Typography

**Font Family:**
- Primary: Inter (via Google Fonts CDN)
- Fallback: system-ui, -apple-system, sans-serif

**Type Scale:**
- Page Title (h1): text-3xl, font-bold (Discord Verification / You're Verified)
- Section Heading (h2): text-xl, font-semibold (rare usage)
- Body Text: text-base, font-normal, leading-relaxed
- Small Print: text-sm (retention details, powered by text)
- Button Text: text-base, font-semibold

**Hierarchy Notes:**
- Use bold weight (font-semibold/font-bold) for critical information like "hashed IP" and data retention period
- Maintain consistent line-height (leading-relaxed) for comfortable reading of consent details

---

### B. Layout System

**Spacing Units:** Use Tailwind units of 4, 6, 8, 12, 16, 20, 24
- Component padding: p-6 to p-8
- Section spacing: space-y-6 for vertical rhythm
- Card margins: mt-16 to mt-24 for page centering
- List items: space-y-3 for comfortable scanning

**Container Strategy:**
- Max-width: max-w-2xl (640px) for optimal reading and focus
- Horizontal centering: mx-auto
- Viewport padding: px-6 for mobile comfort
- Vertical centering: Consent page uses min-h-screen with flex centering

**Grid System:** Not applicable (single-column, card-based layout)

---

### C. Component Library

**Core UI Elements:**

1. **Primary Card Container**
   - Rounded corners (rounded-xl)
   - Subtle shadow (shadow-lg)
   - Clean background with padding (p-8 md:p-12)
   - Center-aligned on viewport

2. **Information List (Consent Details)**
   - Bullet points with clear left alignment
   - Icon support optional (checkmark or lock icons from Heroicons)
   - Spacing between items (space-y-3)
   - Bold inline emphasis for key terms (IP hash, retention, Discord ID)

3. **Primary Action Button (Verify with Discord)**
   - Discord brand blue accent
   - Bold text (font-semibold)
   - Generous padding (px-8 py-3)
   - Rounded corners (rounded-lg)
   - Full-width on mobile, auto width on desktop
   - Clear hover state (slight darkening)
   - Prominent placement after consent information

4. **Success State (Verification Complete)**
   - Centered layout
   - Large success icon (Heroicons check-circle, text-5xl size)
   - Green accent for positive confirmation
   - Brief, reassuring message
   - No additional actions needed (implicit "close tab" instruction)

**Typography Elements:**
- Paragraph blocks with comfortable spacing (space-y-4)
- Inline code/emphasis for technical terms
- Small footer text for "Powered by" attribution

**Forms:** Not applicable (OAuth flow handled externally)

**Data Displays:**
- Unordered list for consent bullet points
- Strong tags for emphasis within paragraphs
- Retention period displayed prominently (dynamic from config)

**Overlays:** Not applicable

---

### D. Animations

**Policy:** No animations

**Rationale:** This is a security-focused verification tool where stability and professionalism trump visual flourish. Users need to trust the process, and animations could detract from that seriousness.

**Interaction States:**
- Button hover: Subtle color darkening only
- No transitions, fades, or motion effects
- Instant page loads preferred

---

## Page-Specific Implementation

### Consent/Landing Page
- **Layout:** Single centered card on clean background
- **Hierarchy:** Title → Explanation paragraph → Bullet list (consent details) → CTA button → Footer
- **Content density:** Information-rich but scannable with clear visual breaks
- **CTA prominence:** Primary button with adequate whitespace before/after

### Success Page  
- **Layout:** Minimal centered content
- **Elements:** Success icon, confirmation heading, brief message
- **Purpose:** Quick visual confirmation, no further action required
- **Tone:** Positive, reassuring, aligned with Discord's friendly aesthetic

---

## Brand Alignment

**Discord Integration:**
- Use Discord's brand blue (#5865F2) for primary actions and accents
- Complement with neutral grays for text and backgrounds
- Success state uses green for positive reinforcement
- Maintain professional distance: not mimicking Discord UI, but harmonizing with it

**Trust Indicators:**
- Clean, uncluttered layouts
- Professional typography
- Clear information hierarchy
- Explicit consent language
- Security-focused messaging (hashed, temporary, deletable)