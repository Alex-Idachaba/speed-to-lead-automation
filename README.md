# Speed-to-Lead Automation

**Pattern:** Routing

Instant lead response automation — a personalized first-touch email and qualifying questions the moment a new lead comes in, with no staffing required outside business hours.

## Problem

Leads contacted within minutes convert far better than leads that wait even a few hours, but most small businesses can't staff someone to watch the inbox around the clock. A lead who fills out a form after hours usually waits until the next business day for a reply.

## Build

Two decoupled n8n workflows. The first fires the moment a new lead arrives, sending an immediate personalized email with qualifying questions — gathering the information a salesperson would normally ask for on a first call, before a human is involved. The second handles replies, matching them to the correct lead conversation using Gmail's `threadId` so context stays attached to the right person even when replies arrive out of order or after a delay.

## Outcome

Every lead gets a fast, personalized response with no after-hours staffing, and qualifying answers are often already collected by the time a salesperson picks up the conversation.

## Reliability Notes

The `threadId`-based matching is the key reliability piece: it keeps replies correctly attached to their originating lead even under real-world timing irregularities, rather than relying on fragile assumptions like message order.

## Stack

n8n, Gmail (send + threading)

## Status

Complete.
