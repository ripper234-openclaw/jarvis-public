# Tooltip Best Practices

## Timing
- **Delay before show**: 300ms (avoids accidental triggers from mouse passing over)
- **Fade in**: 150-200ms opacity + slight translateY (2-4px)
- **Fade out**: immediate on mouse leave (no delay), 150ms transition

## Direction
- Default: appear **above** the element (bottom → up motion feels natural, like a bubble rising)
- If near top of viewport: flip to below
- Slide direction should match position: above = slide up, below = slide down

## Animation
- Combine opacity fade + small transform (translateY 4px)
- Never snap in/out (no `display:none` toggle without transition)
- Use `transition-delay` on hover, not on unhover

## Content
- Max 1-2 short sentences
- Supplement the visible text, don't repeat it
- No critical info in tooltips (not all users will discover them)

## Sizing
- Width: 180-220px for multi-line
- Padding: 0.5-0.75rem
- Font: slightly smaller than body (0.7-0.75rem)
- Softer shadow than cards (less dramatic)

## Arrow/caret
- Small triangle (5-6px) pointing toward the trigger element
- Same color as tooltip background
- Centered on the trigger

## Mobile
- Tooltips don't work well on touch (no hover)
- Consider: tap to show, tap elsewhere to dismiss
- Or: skip tooltips on mobile, show info inline instead

## Don'ts
- Don't use for essential information
- Don't make tooltips too wide (max ~250px)
- Don't animate with bounce or spring effects
- Don't show multiple tooltips simultaneously
- Don't put interactive content (links, buttons) in tooltips
