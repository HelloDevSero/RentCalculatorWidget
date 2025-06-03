# Keep LA Housed Rent Calculator Widget - Technical Specification Sheet

## Document Overview

This specification sheet defines all configurable elements, technical requirements, and customization options for the Keep LA Housed Rent Calculator Widget. Use this document to understand what can be modified, what's fixed, and how to implement changes.

**Version**: 1.0 Production Ready  
**Last Updated**: Current  
**Target Platform**: Web embedding (Squarespace, WordPress, static sites)  
**Dependencies**: None (self-contained)

---

## Core Functionality Specifications

### Calculation Engine

#### Keep LA Housed Formula
```javascript
// CONFIGURABLE: Can be modified for policy changes
calculateProgressiveFormula(rent, inflation) {
    const increasePercent = Math.min(inflation * 0.6, 3); // 60% of CPI, 3% cap
    const increaseAmount = rent * (increasePercent / 100);
    return {
        newRent: rent + increaseAmount,
        increaseAmount,
        increasePercent
    };
}
```

**Configuration Options:**
- `inflation * 0.6` → Change multiplier (currently 60% of CPI)
- `3` → Change maximum cap percentage
- Formula can be completely replaced if policy changes

#### Current LARSO Formula
```javascript
// CONFIGURABLE: Update when current policy changes
calculateCurrentLARSO(rent, inflation, utilitiesIncluded) {
    let increasePercent = 3; // Base rate
    if (utilitiesIncluded) increasePercent += 2; // Utility surcharge
    
    const percentIncrease = rent * (increasePercent / 100);
    const monthlySurcharges = 4.44; // RSO + SCEP fees
    const totalIncrease = percentIncrease + monthlySurcharges;
    
    return { newRent: rent + totalIncrease, increaseAmount: totalIncrease, increasePercent };
}
```

**Configuration Options:**
- `3` → Base percentage rate
- `2` → Utility surcharge percentage  
- `4.44` → Monthly fee amount (RSO $1.61 + SCEP $2.83)

#### Housing Department Formula
```javascript
// CONFIGURABLE: Update based on final policy proposal
calculateModerateFormula(rent, inflation) {
    const increasePercent = Math.max(2, Math.min(inflation, 5)); // 2% floor, 5% cap
    const increaseAmount = rent * (increasePercent / 100);
    return { newRent: rent + increaseAmount, increaseAmount, increasePercent };
}
```

**Configuration Options:**
- `2` → Minimum percentage floor
- `5` → Maximum percentage cap

### Input Validation

#### Rent Validation Rules
```javascript
// CONFIGURABLE: Adjust for different markets or policies
const VALIDATION_RULES = {
    rent: {
        min: 500,    // Minimum valid rent
        max: 25000,  // Maximum valid rent
        required: true
    }
};
```

**Customization Notes:**
- Adjust min/max for different geographic markets
- Error messages automatically update based on these values

#### Inflation Rate Configuration
```javascript
// CONFIGURABLE: Default inflation assumption
inflationRate: 2.8, // Current LA area average
```

**Range**: 0.0% to 10.0% (0.1% increments)  
**Default**: 2.8% (based on recent LA CPI data)

---

## Content and Copy Specifications

### Bilingual Content Structure

All user-facing text is stored in translation objects and can be easily modified:

#### English Content (en)
```javascript
en: {
    // Welcome Section
    welcomeTitle: "Compare LA Rent Control Formulas",
    welcomeSubtitle: "Enter your current rent to see how different proposals would affect your housing costs",
    rentLabel: "Your Current Monthly Rent",
    utilitiesText: "My landlord provides gas and/or electricity",
    calculateBtn: "View Comparison",
    
    // Calculator Section  
    calculatorTitle: "Rent Control Calculator",
    editBtn: "Edit",
    keepLAHousedTitle: "Keep LA Housed",
    currentLARSOTitle: "Current LARSO",
    housingDeptTitle: "Housing Dept",
    
    // Validation Messages
    rentTooLow: "Rent must be at least $500 per month",
    rentTooHigh: "Rent cannot exceed $25,000 per month",
    rentRequired: "Please enter your monthly rent amount",
    
    // Time Periods
    oneYear: "1 Year",
    threeYears: "3 Years", 
    fiveYears: "5 Years",
    tenYears: "10 Years",
    
    // Results
    savingsTitle: "Annual Savings",
    savingsPeriod: "with Keep LA Housed formula",
    month: "month",
    utilitiesIncluded: "utilities included"
}
```

#### Spanish Content (es)
```javascript
es: {
    welcomeTitle: "Compara las Fórmulas de Control de Alquiler de LA",
    welcomeSubtitle: "Ingresa tu alquiler actual para ver cómo las diferentes propuestas afectarían tus costos de vivienda",
    rentLabel: "Tu Alquiler Mensual Actual",
    utilitiesText: "Mi arrendador paga gas y/o electricidad",
    calculateBtn: "Ver Comparación",
    // ... complete Spanish translations
}
```

**Customization Process:**
1. Modify text in translation objects
2. All UI elements update automatically
3. Add new languages by creating additional translation objects
4. Error messages inherit validation ranges automatically

### Formula Labels and Branding

#### Policy Approach Names
```javascript
// CONFIGURABLE: Update if branding or names change
keepLAHousedTitle: "Keep LA Housed",      // Coalition name
currentLARSOTitle: "Current LARSO",       // Current policy name  
housingDeptTitle: "Housing Dept",         // Alternative proposal name
```

**Options:**
- Change "Keep LA Housed" if organization rebrands
- Update "Housing Dept" to reflect actual proposal source
- Modify "Current LARSO" if policy naming changes

#### Visual Branding
```css
/* CONFIGURABLE: Coalition brand colors */
--primary-color: #0303ab;    /* Keep LA Housed blue */
--secondary-color: #ff914d;  /* Keep LA Housed orange */
--neutral-color: #666666;    /* Housing Dept gray */
```

**Color Usage:**
- Primary: Keep LA Housed elements, buttons, focus states
- Secondary: Progressive formula highlights, savings displays
- Neutral: Housing Department formula elements

---

## Visual Design Specifications

### Layout Configuration

#### Container Sizing
```css
/* CONFIGURABLE: Widget maximum width */
.widget-container {
    max-width: 480px;  /* Adjustable for different layouts */
    margin: 0 auto;
}
```

#### Responsive Breakpoints
```css
/* CONFIGURABLE: Mobile breakpoint */
@media (max-width: 900px) { /* Tablet adjustments */ }
@media (max-width: 600px) { /* Mobile adjustments */ }
```

### Chart Configuration

#### Time Period Options
```javascript
// CONFIGURABLE: Available projection periods
projectionYears: [1, 3, 5, 10] // Can add/remove options
```

#### Chart Styling
```javascript
// CONFIGURABLE: Chart appearance
const lines = [
    { data: "progressive", color: "#ff914d", width: 3 },  // Keep LA Housed
    { data: "current", color: "#0303ab", width: 3 },      // Current LARSO
    { data: "moderate", color: "#666666", width: 3 }      // Housing Dept
];
```

**Customization Options:**
- Line colors (matches CSS color variables)
- Line thickness
- Point markers
- Grid styling

---

## Technical Integration Specifications

### Embedding Requirements

#### HTML Implementation
```html
<!-- REQUIRED: Single file embed -->
<div id="rent-calculator-container">
    <!-- Paste complete widget HTML here -->
</div>
```

#### Platform Compatibility
- **Squarespace**: Code Block or Custom HTML injection
- **WordPress**: HTML block or Custom HTML widget  
- **Static Sites**: Direct HTML inclusion
- **Other CMS**: Any platform supporting custom HTML/CSS/JS

#### Performance Requirements
- **Load Time**: <100ms initial display
- **Memory Usage**: <5MB peak usage
- **Browser Support**: Modern browsers (Chrome 88+, Firefox 87+, Safari 14+)

### File Structure
```
widget-complete.html
├── HTML Structure (semantic, accessible)
├── CSS Styles (embedded, namespaced)
└── JavaScript (embedded, self-contained)
```

**Dependencies**: None (completely self-contained)  
**External Requests**: None (privacy-compliant)  
**Storage**: None (no localStorage/sessionStorage)

---

## Accessibility Specifications

### WCAG 2.1 AA Compliance

#### Focus Management
```css
/* CONFIGURABLE: Focus indicator styling */
*:focus-visible {
    outline: 2px solid var(--primary-color);
    outline-offset: 2px;
}
```

#### Screen Reader Support
- All interactive elements have proper ARIA labels
- Error messages announced via `aria-live="polite"`
- Form inputs have accessible descriptions
- Chart data has text alternatives

#### Keyboard Navigation
- Tab order follows logical flow
- Arrow keys navigate between related controls
- Escape key closes modal dialogs
- Enter key activates buttons

#### High Contrast Support
```css
@media (prefers-contrast: high) {
    /* Enhanced contrast styling */
}
```

#### Reduced Motion Support
```css
@media (prefers-reduced-motion: reduce) {
    /* Disabled animations */
}
```

---

## Configuration Management

### Easy Modification Points

#### Policy Formula Updates
**Location**: JavaScript calculation methods  
**Frequency**: When policies change  
**Complexity**: Low (single number/percentage changes)

```javascript
// Example: Change Keep LA Housed cap from 3% to 2.5%
const increasePercent = Math.min(inflation * 0.6, 2.5); // Changed from 3
```

#### Content Updates
**Location**: Translation objects  
**Frequency**: As needed for messaging refinement  
**Complexity**: Very Low (text replacement)

```javascript
// Example: Update welcome message
welcomeTitle: "New Title Here", // Replace existing text
```

#### Visual Branding Updates
**Location**: CSS custom properties  
**Frequency**: Rare (rebrandings)  
**Complexity**: Low (color code changes)

```css
/* Example: Change primary color */
--primary-color: #123456; /* Replace color code */
```

### Advanced Customization Options

#### New Language Addition
1. Create new translation object (e.g., `ko` for Korean)
2. Add language toggle button to HTML
3. Include language in dropdown/selection

#### Additional Policy Formulas
1. Create new calculation method
2. Add to calculations object
3. Update chart drawing and table generation
4. Add corresponding color and labeling

#### Modified Input Fields
1. Update HTML form structure
2. Modify validation rules
3. Update calculation methods to use new inputs

---

## Data and Privacy Specifications

### Data Handling
- **User Input**: Processed locally, never transmitted
- **Calculations**: Performed client-side only
- **Storage**: No data persistence (session-based only)
- **Analytics**: None implemented (organization choice)

### Privacy Compliance
- **GDPR**: Compliant (no data collection)
- **CCPA**: Compliant (no personal data processing)
- **COPPA**: Compliant (no user registration/tracking)

### Security Features
- **XSS Prevention**: Uses `textContent` instead of `innerHTML`
- **Input Sanitization**: Number validation prevents injection
- **External Dependencies**: None (zero attack surface)
- **Content Security Policy**: Compatible with strict CSP

---

## Maintenance and Support Specifications

### Update Procedures

#### Content Updates (Non-Technical)
1. Modify translation objects in JavaScript section
2. Save and re-embed updated HTML
3. Test across key browsers
4. Deploy to partner sites

#### Formula Updates (Technical)
1. Update calculation methods
2. Verify accuracy with test cases
3. Update any related labeling/copy
4. Full testing cycle including accessibility
5. Coordinate deployment across coalition

#### Visual Updates (Design)
1. Modify CSS custom properties
2. Test responsive behavior
3. Verify accessibility compliance
4. Update across all embedded instances

### Version Control
- **Current Version**: 1.0 Production Ready
- **Change Log**: Document all modifications with dates
- **Backup Strategy**: Keep working versions before major changes
- **Testing Protocol**: Cross-browser and accessibility testing for all updates

### Support Requirements
- **Technical Expertise**: HTML/CSS/JavaScript knowledge for modifications
- **Testing Capacity**: Multi-browser and device testing capability  
- **Deployment Coordination**: Ability to update across partner organization sites
- **Accessibility Validation**: Screen reader and keyboard testing for changes

---

## Quality Assurance Specifications

### Testing Checklist

#### Functional Testing
- [ ] All calculation formulas produce expected results
- [ ] Input validation prevents invalid submissions
- [ ] Language switching works completely
- [ ] Chart and table display accurate data
- [ ] Mobile responsive layout functions correctly
- [ ] Settings panel operates properly

#### Accessibility Testing
- [ ] Screen reader announces all content correctly
- [ ] Keyboard navigation reaches all interactive elements
- [ ] Focus indicators clearly visible
- [ ] Error messages announced appropriately
- [ ] High contrast mode functions
- [ ] Color information not required for understanding

#### Cross-Browser Testing
- [ ] Chrome (desktop and mobile)
- [ ] Firefox (desktop and mobile)
- [ ] Safari (desktop and mobile)
- [ ] Edge (desktop)
- [ ] Graceful degradation in older browsers

#### Performance Testing
- [ ] Load time under 100ms
- [ ] Smooth chart animations
- [ ] Responsive resize behavior
- [ ] Memory usage stable over time
- [ ] No JavaScript errors in console

### Error Handling Verification
- [ ] Invalid rent amounts show appropriate errors
- [ ] Missing translation keys fall back to English
- [ ] Calculation errors display user-friendly messages
- [ ] Network issues don't break functionality
- [ ] Extreme input values handled gracefully

---

## Implementation Guide

### Quick Start Deployment
1. **Copy HTML**: Use complete widget code as provided
2. **Embed in Site**: Paste into Code Block or HTML area
3. **Test Functionality**: Verify all features work in target environment
4. **Mobile Check**: Test on actual mobile devices
5. **Go Live**: Deploy to production site

### Customization Workflow
1. **Identify Changes**: Use this spec to locate modification points
2. **Make Changes**: Edit appropriate sections (CSS, JavaScript, or HTML)
3. **Test Locally**: Verify changes work as expected
4. **Accessibility Check**: Ensure modifications maintain compliance
5. **Deploy**: Update embedded code across coalition sites

### Troubleshooting Common Issues
- **Widget Not Loading**: Check for JavaScript errors in browser console
- **Styling Conflicts**: Ensure CSS namespacing is intact (`.kla-rent-calculator`)
- **Mobile Issues**: Verify responsive meta tag is present
- **Translation Problems**: Check for missing or malformed translation keys
- **Calculation Errors**: Verify formula modifications maintain proper syntax

---

## Support and Contact Information

### Technical Support
- **Code Modifications**: Requires HTML/CSS/JavaScript developer
- **Content Updates**: Can be done by non-technical users with guidance
- **Accessibility Compliance**: Requires accessibility testing expertise
- **Performance Optimization**: May require front-end development experience

### Change Request Process
1. **Document Requirements**: Specify exact changes needed
2. **Impact Assessment**: Determine if changes affect calculations, accessibility, or functionality
3. **Implementation**: Make changes following this specification
4. **Quality Assurance**: Complete testing checklist
5. **Deployment**: Coordinate updates across coalition partners

### Emergency Support Scenarios
- **Policy Changes**: Rapid formula updates during active legislation
- **Bug Fixes**: Critical errors affecting user experience or data accuracy
- **Accessibility Issues**: Problems affecting compliance or user access
- **Performance Problems**: Significant slowdowns or failures

---

This specification sheet provides complete documentation for understanding, modifying, and maintaining the Keep LA Housed Rent Calculator Widget. Use it to guide any changes while ensuring the tool continues to serve the coalition's organizing goals effectively.