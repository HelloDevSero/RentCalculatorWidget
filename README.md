# Keep LA Housed Rent Calculator Widget

A bilingual, accessible rent control policy comparison tool for housing justice organizing in Los Angeles.

[![Production Ready](https://img.shields.io/badge/status-production%20ready-green)](#)
[![WCAG 2.1 AA](https://img.shields.io/badge/accessibility-WCAG%202.1%20AA-blue)](#)
[![Mobile Optimized](https://img.shields.io/badge/mobile-optimized-brightgreen)](#)
[![No Dependencies](https://img.shields.io/badge/dependencies-none-orange)](#)

## Overview

The Keep LA Housed Rent Calculator Widget enables Los Angeles tenants to compare how different rent control proposals would affect their actual housing costs over time. Built specifically for the Keep LA Housed Coalition's organizing efforts, this tool transforms complex policy debates into personalized, tangible impacts.

### What It Does

- **Personalized Calculations**: Users input their rent and see exact dollar impacts under three policy scenarios
- **Multi-Year Projections**: Interactive charts show 1, 3, 5, or 10-year rent progression
- **Policy Comparison**: Side-by-side analysis of Keep LA Housed, Current LARSO, and Housing Department proposals
- **Bilingual Support**: Complete English and Spanish translations with cultural appropriateness
- **Accessibility First**: WCAG 2.1 AA compliant with screen reader and keyboard support

### Key Features

✅ **Zero Dependencies** - Self-contained HTML file, no external libraries  
✅ **Privacy-First** - All calculations client-side, no data transmission  
✅ **Mobile Optimized** - Responsive design prioritizes smartphone users  
✅ **Easy Embedding** - Works with Squarespace, WordPress, and static sites  
✅ **Professional Quality** - Enterprise-level reliability for policy discussions  
✅ **Coalition Ready** - Designed for deployment across 80+ partner organizations  

---

## Quick Start

### For Coalition Partners (Non-Technical)

1. **Get the Code**: Copy the complete HTML code from your Keep LA Housed contact
2. **Embed in Your Site**: 
   - **Squarespace**: Add a Code Block, paste the HTML
   - **WordPress**: Add HTML block, paste the code  
   - **Other Sites**: Contact your web administrator
3. **Test**: Verify the calculator works on your site
4. **Go Live**: The widget is ready for your visitors

### For Developers

```html
<!-- Simple embedding - paste this complete HTML file -->
<!DOCTYPE html>
<html>
<!-- Full widget code here -->
</html>
```

**Requirements**: None (self-contained)  
**Browser Support**: Modern browsers (Chrome 88+, Firefox 87+, Safari 14+)  
**Performance**: <100ms load time, mobile optimized

---

## How It Works

### Policy Calculations

The widget compares three rent control approaches using actual policy formulas:

#### Keep LA Housed Formula
```
Annual Increase = MIN(CPI × 0.6, 3%)
- No utility surcharges
- No monthly fees  
- No rent banking
- Already implemented in LA County unincorporated areas
```

#### Current LARSO System  
```
Base Increase = 3%
+ Utility Surcharge = 1% for gas, 1% for electricity
+ Monthly Fees = $4.44 ($53.28 annually)
+ Additional occupant increases possible
+ Rent banking allowed
```

#### Housing Department Proposal
```
Annual Increase = MAX(2%, MIN(CPI, 5%))
- 2% minimum floor
- 5% maximum cap
- Based on inflation with reasonable bounds
```

### User Experience Flow

1. **Input Rent**: User enters current monthly rent ($500-$25,000 range)
2. **Utility Configuration**: Option to include gas/electricity provided by landlord
3. **View Comparison**: Side-by-side results showing new rent under each policy
4. **Explore Projections**: Interactive charts and tables for different time periods
5. **See Savings**: Annual savings calculation with Keep LA Housed formula
6. **Language Toggle**: Switch between English and Spanish instantly
7. **Share Results**: Professional charts suitable for social media and policy discussions

---

## Features Guide

### Bilingual Support

**Complete Translation Coverage**:
- All interface elements available in English and Spanish
- Error messages in both languages
- Cultural appropriateness for LA Latino community
- Robust fallback system prevents broken interfaces

**Language Switching**:
- Instant content replacement (no page refresh)
- Maintains user input when switching languages
- Automatic error message re-validation in new language

### Accessibility Features

**WCAG 2.1 AA Compliant**:
- Screen reader optimized with proper ARIA labels
- Keyboard navigation including arrow key support between related controls
- High contrast mode support
- Reduced motion support for users with vestibular disorders
- Focus indicators clearly visible for keyboard users

**Input Validation**:
- Real-time validation with accessible error announcements
- Clear, actionable error messages
- Prevention of invalid calculations that could damage credibility

### Mobile Optimization

**Responsive Design**:
- Mobile-first layout adapts to any screen size
- Touch-optimized interface elements
- Smooth chart performance on smartphones
- Readable typography across all devices

**Performance**:
- ResizeObserver-based chart optimization
- High-DPI display support for crisp visuals
- Memory management prevents performance degradation
- Optimized for social media sharing

### Interactive Visualizations

**Chart Display**:
- Line graph showing rent progression over time
- Color-coded for easy policy comparison
- Interactive time period selection (1, 3, 5, 10 years)
- Professional quality suitable for presentations

**Data Tables**:
- Year-by-year breakdown for detailed analysis
- Accessible to screen readers
- Sortable and copy-friendly for policy documents

---

## Technical Specifications

### Architecture

**Self-Contained Design**:
- Single HTML file with embedded CSS and JavaScript
- No external dependencies or API calls
- All calculations performed client-side
- No data storage or transmission

**Browser Compatibility**:
- **Full Support**: Chrome 88+, Firefox 87+, Safari 14+, Edge 88+
- **Graceful Degradation**: Older browsers maintain basic functionality
- **Mobile**: Optimized for iOS Safari and Android Chrome

### Security & Privacy

**Privacy-First Design**:
- Zero data collection or transmission
- No cookies or local storage
- No external analytics or tracking
- GDPR/CCPA compliant by design

**Security Features**:
- XSS prevention through proper content handling
- Input sanitization prevents injection attacks
- No external dependencies eliminate supply chain risks
- Content Security Policy compatible

---

## Customization Guide

### Easy Modifications

#### Policy Formula Updates
```javascript
// Example: Change Keep LA Housed cap from 3% to 2.5%
const increasePercent = Math.min(inflation * 0.6, 2.5); // Line ~850
```

#### Content Changes
```javascript
// Update welcome message
welcomeTitle: "Your New Title Here", // Line ~450
```

#### Visual Branding
```css
/* Change primary color */
--primary-color: #your-color-here; /* Line 15 */
```

### Advanced Customization

#### Adding New Languages
1. Create translation object (e.g., `ko` for Korean)
2. Add language button to HTML
3. Include in language switching logic

#### New Policy Formulas
1. Add calculation method
2. Update results display
3. Modify chart and table generation

#### Additional Input Fields
1. Update HTML form structure  
2. Modify validation rules
3. Update calculation methods

---

## Deployment Guide

### Coalition Partner Deployment

#### Squarespace Sites
1. Navigate to page where you want the calculator
2. Add a Code Block from the content menu
3. Paste the complete HTML code
4. Save and publish

### Testing Checklist

Before going live, verify:
- [ ] Calculator loads without errors
- [ ] All three policy calculations display correctly
- [ ] Language switching works completely
- [ ] Charts and tables render properly on mobile
- [ ] Input validation shows appropriate errors
- [ ] Keyboard navigation functions properly
- [ ] Settings panel opens and inflation slider works

### Troubleshooting

**Calculator Won't Load**:
- Check browser console for JavaScript errors
- Ensure complete HTML code was copied
- Verify platform supports custom HTML/CSS/JS

**Styling Issues**:
- Confirm CSS namespacing is intact (`.kla-rent-calculator`)
- Check for theme conflicts overriding styles
- Test in different browser/device combinations

**Mobile Problems**:
- Verify responsive meta tag is present in page
- Test actual mobile devices, not just browser resize
- Check for platform-specific mobile style conflicts

---

## Support & Maintenance

### Regular Maintenance

**Policy Updates** (when formulas change):
- Update calculation methods in JavaScript
- Test accuracy with known examples
- Coordinate deployment across coalition partners

**Content Updates** (messaging refinements):
- Modify translation objects
- Test in both languages
- Ensure accessibility compliance maintained

**Visual Updates** (branding changes):
- Update CSS custom properties
- Test responsive behavior
- Verify high contrast mode compatibility

### Getting Help

**For Coalition Partners**:
- Contact your Keep LA Housed coordinator
- Check with your organization's web administrator
- Review this README for common solutions

**For Technical Issues**:
- Provide browser console errors if any
- Include description of what's not working
- Note which platform you're using (Squarespace, WordPress, etc.)

**For Policy Questions**:
- All calculations verified against official policy documents
- Formula sources documented in code comments
- Keep LA Housed policy team can clarify assumptions

---

## Coalition Use Cases

### Community Organizing

**Town Halls & Meetings**:
- Interactive tool for explaining policy differences
- Generate specific examples for discussion
- Professional presentation suitable for community leaders

**Door-to-Door Canvassing**:
- Tablet/smartphone friendly for field use
- Quick calculations during voter conversations
- Shareable results for follow-up

### Policy Advocacy

**City Council Engagement**:
- Tenants bring specific dollar amounts to meetings
- Professional charts for staff presentations
- Evidence-based testimony rather than abstract arguments

**Media Relations**:
- Generate illustrative examples for journalists
- Professional quality suitable for TV/online coverage
- Consistent calculations across all coalition communications

### Digital Organizing

**Social Media Campaigns**:
- Personalized results create compelling content
- Professional charts optimized for sharing
- Bilingual capability reaches diverse audiences

**Email & Web Outreach**:
- Embed in newsletters and websites
- Educational resource for supporter engagement
- Lead generation for deeper organizing conversations

---

## Development Philosophy

### Housing Justice First

This tool was built with the understanding that housing is a human right and that technology should serve organizing, not replace it. Every design decision prioritizes:

- **Accessibility**: Ensuring no tenant is excluded from policy understanding
- **Accuracy**: Maintaining credibility in policy discussions
- **Simplicity**: Making complex policy accessible to diverse communities
- **Reliability**: Supporting rather than undermining coalition credibility

### Proven Policy Focus

The calculator emphasizes that Keep LA Housed's formula isn't theoretical—it's proven policy successfully implemented in LA County's unincorporated areas since January 2025, affecting over 100,000 rental units. This evidence-based approach strengthens policy arguments and demonstrates feasibility.

### Coalition-Centered Design

Built for a movement, not just an organization. Features like easy embedding, consistent calculations, and professional presentation support the Keep LA Housed Coalition's network of 80+ partner organizations working together for housing justice.

---

## Contributing

### Feedback Welcome

As Keep LA Housed Coalition partners use this tool, feedback helps improve effectiveness:

- **User Experience**: What works well? What's confusing?
- **Policy Accuracy**: Any questions about calculations or assumptions?
- **Technical Issues**: Bugs, performance problems, or compatibility issues?
- **Feature Requests**: Additional functionality that would support organizing?

### Future Enhancements

Potential improvements based on organizing needs:

- **Additional Jurisdictions**: Adapt for other cities if coalition expands
- **Enhanced Analytics**: Usage tracking if coalition desires insights
- **Integration Options**: Connect with organizing signup or donation systems
- **Policy Monitoring**: Framework for tracking actual impacts if policies implemented

---

## License & Usage

### Coalition Use

This tool is developed specifically for the Keep LA Housed Coalition and its partner organizations fighting for housing justice in Los Angeles. Coalition partners are encouraged to:

- Embed the widget on organizational websites
- Use in community education and organizing
- Share results in policy advocacy
- Distribute through social networks
- Modify content for organizational messaging needs

### Attribution

When using this tool, please maintain attribution to the Keep LA Housed Coalition as the source of policy analysis and calculations.

### Policy Accuracy

All calculations are verified against official policy documents and LA County's implementation. Formula sources are documented in code comments. Questions about policy assumptions should be directed to Keep LA Housed policy staff.

---

## Changelog

### Version 1.0 (Production Ready)
- ✅ Complete bilingual English/Spanish support
- ✅ Input validation with accessible error messages  
- ✅ ResizeObserver-optimized chart performance
- ✅ Enhanced keyboard navigation and WCAG 2.1 AA compliance
- ✅ High-DPI display support
- ✅ Error boundaries and graceful failure handling
- ✅ Professional presentation suitable for policy discussions
- ✅ Squarespace-optimized embedding
- ✅ Zero external dependencies
- ✅ Mobile-first responsive design

---

## Contact

For questions about this tool or the Keep LA Housed Coalition's work:

TBD

---

*This tool represents the power of technology in service of housing justice. By making complex policy accessible and personally relevant, we strengthen our collective fight for affordable housing in Los Angeles.*

**Ready to embed? Start with the Quick Start guide above. Ready to organize? Let's build housing justice together.** 🏠✊