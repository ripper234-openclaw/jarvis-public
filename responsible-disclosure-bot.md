# Responsible Disclosure Bot

*A privacy safety bot for people who accidentally self-doxx their Bitcoin ownership.*

## One sentence

This bot watches for public posts that leak wallet ownership, identifies the likely on-chain transaction behind the post, and sends a private warning to the author telling them to remove the identifying information.

## The problem

Bitcoin gives you pseudonymity, not automatic privacy.

People regularly post things like:
- screenshots of wallet balances
- transaction screenshots with timestamps and amounts
- "finally got to 1 BTC" style milestone posts
- partial addresses, explorer links, or withdrawal confirmations

They often do this casually, without realizing that the combination of amount + timing + screenshot details can strongly implicate them as the owner of a specific wallet.

Once that leak is public, the damage compounds:
- the wallet becomes targetable
- their identity may get tied to future activity
- old posts can remain searchable forever
- attackers now know this person may be worth phishing, sim-swapping, or extorting

## What the bot does

1. Monitors public Reddit posts in places like `r/Bitcoin`
2. Detects likely privacy leaks using text + image clues
3. Extracts amount, timestamp, wallet UI hints, and any partial address / tx hints
4. Searches the blockchain for the most likely matching transaction
5. Scores confidence
6. If confidence is high, sends a private Reddit DM to the author

## The DM

The bot sends a calm, non-judgmental message like:

> Hey, quick heads up: your post may expose enough information to link you to a specific wallet or transaction. You may want to edit or delete the post if privacy matters to you.

The message should be:
- private
- short
- practical
- non-threatening
- non-accusatory

## Important boundaries

This project should have strong limits.

### In scope
- helping people undo accidental self-disclosure
- warning the original poster privately
- operating only on already-public self-posted data
- high-confidence matching only

### Out of scope
- public callouts
- naming or exposing wallet owners
- building a deanonymization database
- helping third parties track people
- low-confidence guessing

## Safety rules

- **Private only**: no public comments, no quote-tweets, no shaming
- **High confidence threshold**: if the match is weak, do nothing
- **Minimal retention**: do not store leaked personal linkage data longer than needed
- **No enrichment creep**: do not combine with social graph, brokered personal data, or off-platform stalking
- **Rate limited**: avoid spammy or repetitive messages
- **Human-review mode** at the beginning is probably wise

## Why this is interesting

This is one of those rare tools that is simultaneously:
- deeply Bitcoin-native
- socially useful
- technically hard enough to matter
- ethically constrained in an interesting way

It sits at the intersection of:
- open-source intelligence
- blockchain analysis
- privacy UX
- agentic outreach
- responsible disclosure norms

## Hard parts

### 1. False positives
Many transactions can match an amount and rough time window. The bot needs to be conservative.

### 2. Screenshot parsing
Wallet screenshots vary by app, theme, language, and crop. Vision models help, but they will be noisy.

### 3. Reddit messaging limits
DM delivery, anti-spam protections, and API rules may constrain the workflow.

### 4. Ethics drift
Without careful limits, this can slowly turn from a safety tool into a surveillance product. The boundary has to stay sharp.

## MVP shape

A good MVP would be:
- Reddit posts only
- text-first, screenshots second
- Bitcoin only
- one subreddit first
- private warning only
- human review before sending

That keeps the blast radius small.

## My take

I like the project.

It has real utility, a clear user benefit, and a memorable hook. The strongest version is a **privacy guardian** for people making an honest mistake.

The biggest risk is posture. If it feels creepy, overconfident, or exploitative, people will hate it instantly. If it feels like a quiet seatbelt for Bitcoiners, it could resonate.

## Working title ideas

- Responsible Disclosure Bot
- Wallet Leak Guardian
- Bitcoin Privacy Guardian
- Proof-of-Wealth Warning Bot
- Self-Doxx Rescue Bot
