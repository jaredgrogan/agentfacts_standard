# AgentFacts™ Commercial RPG Character Template

## Overview

This template demonstrates AgentFacts™ commercial capabilities for RPG gaming environments, showcasing how AI companions can operate with verified, limited commerce permissions within virtual economies.

## Key Features

### 🎮 **Gaming-Specific Architecture**
- Game studio-verified AI models
- RPG-focused capabilities and metrics
- ESRB compliance and content rating verification
- Platform integration (Steam, consoles, mobile)

### 💰 **Controlled Virtual Commerce**
- **Transaction Limits**: 1,000 gold per purchase
- **Daily Limits**: 2,500 gold spending cap
- **Weekly Limits**: 10,000 gold budget
- **Category Restrictions**: Equipment/consumables only, no cosmetics
- **Player Oversight**: Approval required for purchases >500 gold

### 🔒 **Trust & Verification**
- Multi-authority verification (Game Studio + ESRB + Platform)
- Cryptographic signatures for capabilities
- Supply chain transparency for game dependencies
- Performance metrics including combat effectiveness

### 📊 **Smart Spending Controls**
- Notification preferences (daily summaries, large purchase alerts)
- Automatic micro-transactions under 100 gold
- Fraud protection and audit trails
- Player can override or adjust limits anytime

## Virtual Economy Integration

### Supported Commerce Activities:
✅ **Equipment purchases** (weapons, armor, tools)  
✅ **Consumable purchases** (potions, food, materials)  
✅ **NPC trading** (verified vendor interactions)  
✅ **Auction house bidding** (competitive marketplace)  
✅ **Item selling** (inventory management)  

❌ **Premium cosmetics** (player-only decisions)  
❌ **Player-to-player trading** (security restrictions)  
❌ **Real money transactions** (virtual currency only)  

## Implementation Guide

### 1. **Customize Template Fields**
Replace all bracketed placeholders with actual values:
- `[Game Studio Name]` → Your studio name
- `[Character_Class]` → Specific character class
- `[player_username]` → Player identifier
- `[gold_amount]` → Starting wealth amount

### 2. **Configure Spending Limits**
Adjust limits based on your game economy:
```json
"spending_authority": {
  "max_transaction_amount": 1000,  // Adjust for your economy
  "daily_spending_limit": 2500,
  "weekly_spending_limit": 10000
}
