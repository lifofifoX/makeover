# DNA Codes

Every normal-mode theme declares: `H#-L#-G#-D#-C#-N#-T#-S#-O#`

## Responsive Transforms

DNA codes implicitly adapt on mobile. Proposals declare desktop DNA only.

| Desktop | Mobile Transform |
|---------|------------------|
| H2 Left Sidebar | → H8 Hamburger |
| H3 Right Sidebar | → H8 Hamburger |
| H5 Split | → H1 Top Bar |
| L3 Sidebar + Content | → L7 Vertical Scroll |
| L5 Magazine | → L2 Hero + List |
| L10 Split Screen | → L3 Stacked |
| G3 4+ Column | → G2 2 Column |
| G7 Horizontal Scroll | → G4 Single Column |
| D1 50/50 Horizontal | → D3 Stacked |
| D4 Media Dominant | → D3 Stacked |

## Header (H1-H12)

| Code | Style | Use When |
|------|-------|----------|
| H1 | Top Bar | Standard apps, dashboards |
| H2 | Left Sidebar | Admin panels, complex navigation |
| H3 | Right Sidebar | Secondary nav, tools |
| H4 | Floating | Minimal, editorial |
| H5 | Split (logo left, nav right edge) | Marketing, landing |
| H6 | Bottom Bar | Mobile-first, unusual |
| H7 | Centered Stack | Portfolios, single-purpose |
| H8 | Hidden/Hamburger | Immersive, gallery |
| H9 | Diagonal/Angled | Bold, experimental |
| H10 | Peripheral | Edges only, content-first |
| H11 | Sticky Minimal | Scrolling pages, blogs |
| H12 | Frame | Border around viewport |

## Home Layout (L1-L12)

| Code | Style | Use When |
|------|-------|----------|
| L1 | Bio + Grid | Portfolios, profiles |
| L2 | Hero + List | Blogs, news |
| L3 | Sidebar + Content | Documentation, wikis |
| L4 | Single Feature | Product focus, landing |
| L5 | Magazine Spread | Editorial, visual content |
| L6 | Dashboard Panels | Data apps, admin |
| L7 | Vertical Scroll Story | Narratives, case studies |
| L8 | Bento Grid | Modern SaaS, Apple-style |
| L9 | Collage/Overlap | Creative, fashion |
| L10 | Split Screen | Comparisons, dual focus |
| L11 | Asymmetric Thirds | Editorial, photography |
| L12 | Floating Islands | Playful, experimental |

## Collection Grid (G1-G12)

| Code | Style | Use When |
|------|-------|----------|
| G1 | 2 Column | Simple galleries |
| G2 | 3 Column | Standard product grids |
| G3 | 4+ Column | Dense catalogs |
| G4 | Single Column List | Feeds, timelines |
| G5 | Table/Rows | Data-heavy, admin |
| G6 | Masonry | Pinterest-style, varied heights |
| G7 | Horizontal Scroll | Featured, carousels |
| G8 | Scattered/Random | Creative, editorial |
| G9 | Featured + Grid | Hero item + supporting |
| G10 | Staggered | Offset rhythm |
| G11 | Filmstrip | Linear sequence |
| G12 | Cluster | Grouped, organic |

## Detail Split (D1-D12)

| Code | Style | Use When |
|------|-------|----------|
| D1 | 50/50 Horizontal | Standard product pages |
| D2 | 50/50 Reversed | Variety, alternating |
| D3 | Stacked Vertical | Mobile-first, long-form |
| D4 | Media Dominant (70/30) | Visual products |
| D5 | Info Dominant (30/70) | Text-heavy, specs |
| D6 | Overlay | Immersive, dramatic |
| D7 | Tabbed Panels | Complex info, categories |
| D8 | Full Bleed + Drawer | Gallery, editorial |
| D9 | Centered Theater | Showcase, specimen |
| D10 | Diptych | Side-by-side comparison |
| D11 | Immersive Scroll | Storytelling |
| D12 | Specimen | Museum-style isolation |

## Card Design (C1-C12)

| Code | Style | Use When |
|------|-------|----------|
| C1 | Square (1:1) | Instagram-style, uniform |
| C2 | Portrait (2:3, 3:4) | People, products |
| C3 | Landscape (16:9, 3:2) | Videos, scenes |
| C4 | Text Row | Lists, dense data |
| C5 | Large Preview | Featured items |
| C6 | Thumbnail + Details | Catalogs, search results |
| C7 | Circular/Rounded | Avatars, profiles |
| C8 | Polaroid/Framed | Nostalgic, photos |
| C9 | Index Card | Archival, catalog |
| C10 | Bleed | Edge-to-edge images |
| C11 | Layered | Stacked, depth |
| C12 | Specimen Slide | Scientific, museum |

## Motion (N1-N9)

**See MOTION.md for full definitions and implementation details.**

| Level | Style |
|-------|-------|
| N1-N2 | Static to subtle (hovers, transitions) |
| N3-N4 | Responsive (scroll-triggered, parallax) |
| N5-N6 | Kinetic/interactive (floating, magnetic, tilt) |
| N7-N9 | Cinematic to chaotic (morphs, glitch, particles) |

## Transition (T1-T12)

View-to-view transitions when navigating between DNA-defined layouts.

| Code | Style | Use When |
|------|-------|----------|
| T1 | Instant Cut | Fast, utilitarian apps |
| T2 | Crossfade | Subtle, professional |
| T3 | Slide Horizontal | Linear navigation, wizards |
| T4 | Slide Vertical | Drill-down, mobile patterns |
| T5 | Shared Element | Card→detail, visual continuity |
| T6 | Scale/Zoom | Focus transitions, gallery |
| T7 | Morph | Fluid, playful apps |
| T8 | Flip/Rotate | Skeuomorphic, card-based |
| T9 | Parallax Layers | Depth, immersive |
| T10 | Reveal/Uncover | Dramatic, editorial |
| T11 | Stagger Elements | Complex layouts, dashboards |
| T12 | Cinematic Sequence | Storytelling, high-end |

## State (S1-S6)

How the design handles non-ideal states. Critical for avoiding generic AI output.

| Code | Style | Use When |
|------|-------|----------|
| S1 | Minimal Skeleton | Fast-loading, clean apps |
| S2 | Branded Loading | Identity-heavy, premium |
| S3 | Progressive Blur | Image-heavy, galleries |
| S4 | Content Placeholder | Data apps, dashboards |
| S5 | Animated Empty | Friendly, consumer apps |
| S6 | Stark Void | Minimalist, editorial |

**Applies to:** Empty states, loading skeletons, error views, offline states.

## Overlay (O1-O8)

Floating and overlay elements that sit above the core layout.

| Code | Style | Use When |
|------|-------|----------|
| O1 | None | Clean, distraction-free |
| O2 | Floating Action Button | Mobile, primary action heavy |
| O3 | Sticky Bottom Bar | E-commerce, CTAs |
| O4 | Announcement Banner | Promos, alerts |
| O5 | Corner Widget | Chat, help, feedback |
| O6 | Slide-out Drawer | Complex tools, filters |
| O7 | Toast Stack | Notifications, confirmations |
| O8 | Command Palette | Power users, keyboard-first |
