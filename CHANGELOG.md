# Changelog

All notable changes to this project are listed here.

## [1.0.0] - 2026-10-16

First complete showcase release.

### Added
- Fictional showcase content: contact details, three coaches (Arjun Mehra, Kavya Iyer, Rohan Sethi) and a footer credit marking the project as a concept
- Boxing media: shadowboxing video on the Fight card, pad-work video and two boxing photos in the gallery, and a "Fight corner" facility
- Photos and videos across the hero, program cards, facilities panel and gallery, with a scroll-driven grey-to-colour "heat" effect
- WhatsApp lead flow: the join form builds a pre-filled message, and all contact details sit in one `GYM` config object
- "Your first 12 weeks" timeline section
- SEO and sharing meta tags (description, Open Graph)
- Trainers stack, facilities list, offer band, BMI gauge, FAQ and join form, all scroll-animated
- Scroll progress bar and floating WhatsApp button

### Changed
- Mobile now pins only two sections (barbell and coaches), and those pins are shorter
- Ember canvas runs only while the hero is visible and uses fewer particles on phones
- Videos load and play only while on screen
- Media compressed from about 50 MB of originals to about 1.9 MB

### Fixed
- Pinned sections overlapping on desktop, caused by ScrollTriggers being created out of page order
- 4 px horizontal scroll on mobile from off-screen barbell plates
- Hero background photo too faint behind the headline
- "Conditioning" title clipped inside its card

### Removed
- Placeholder testimonials and before/after section, which would have shown invented results as real

## [0.1.0] - 2026-10-16

### Added
- Initial scroll-animated page: ember hero, lift ticker, pinned horizontal programs, barbell plate loader, timings table and membership plans
