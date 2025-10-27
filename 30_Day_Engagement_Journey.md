# 30-Day Engagement Journey - Email & SMS Copy
**Project**: Engagement-First Strategy (Path B)
**Owner**: Marketing + Product
**Timeline**: Sprint 0, Week 2
**Target**: Increase 30-day PPC from 1.2 → 2.8

---

## 🎯 Journey Overview

This is a **behavioral trigger-based journey**, NOT a time-based drip campaign.

**Key Principle**: Every message is triggered by user action (or inaction), with personalized next steps based on their current PPC count.

**User Segments**:
- **Segment A**: PPC = 1 (just checking account)
- **Segment B**: PPC = 2 (checking + 1 other product)
- **Segment C**: PPC = 3+ (checking + 2+ other products) ⭐ **Target segment**

**Goal**: Move everyone to Segment C within 30 days.

---

## 📧 Email Templates

### **EMAIL 1: Welcome Email** (T+0 hours)
**Trigger**: Onboarding completed
**Send time**: Immediately
**From**: "Ana from MyBambu" <ana@mybambu.com>
**Subject** (ES): ¡Bienvenido a MyBambu! Tu cuenta está lista 🎉
**Subject** (EN): Welcome to MyBambu! Your account is ready 🎉

**Body** (Spanish):
```
Hola [FirstName],

¡Felicidades! Ya eres parte de la familia MyBambu. 🌴

Tu cuenta está activa y lista para usar. Aquí está lo que tienes:

✓ Cuenta de Ahorro (#[LastFourAccountNumber])
✓ Tarjeta de Débito (llega en 5-7 días)
[IF rewards_activated] ✓ Recompensas Bambu (0 puntos - ¡empieza a ganar!)

---

🎁 GANA $10 ESTA SEMANA

Completa estas tareas simples:

1. Fondea tu cuenta con $10+ → Gana $3
2. Activa tu tarjeta cuando llegue → Gana $5
3. Haz tu primera compra de $5+ → Gana $2

Total: $10 en bonos 💰

[CTA Button: Ver mis tareas]

---

¿Necesitas ayuda?

📱 Descarga la app: [iOS link] [Android link]
💬 Chat en vivo: mybambu.com/chat
📞 Llámanos: 1-855-MYBAMBU (1-855-692-2628)

¡Bienvenido al futuro de la banca!

Ana Rodríguez
Head of Customer Success
MyBambu

P.S. ¿Sabías que clientes con 3+ productos ganan 4× más recompensas? 🚀
```

**Personalization Variables**:
- `[FirstName]`
- `[LastFourAccountNumber]`
- `[IF rewards_activated]` → Conditional block

**Analytics**:
```javascript
analytics.track('email_sent', {
  email_id: 'welcome_email',
  user_segment: 'new_user',
  ppc_count: 1,
  language: 'es'
});

analytics.track('email_opened', { ... });
analytics.track('email_link_clicked', { link: 'view_tasks', ... });
```

---

### **EMAIL 2: Funding Reminder** (T+12 hours)
**Trigger**: Account NOT funded after 12 hours
**Send time**: 8:00am user's local timezone
**Subject** (ES): [FirstName], tu cuenta te espera 👀
**Subject** (EN): [FirstName], your account is waiting 👀

**Body** (Spanish):
```
Hola [FirstName],

Veo que aún no has fondeado tu cuenta. Sin fondos, no puedes:

❌ Usar tu tarjeta de débito
❌ Ganar recompensas
❌ Recibir tus bonos de $10

La buena noticia: ¡Fondear es súper fácil!

Opción 1: Depósito Directo (recomendado)
→ Recibe tu salario 2 días antes
→ BONO EXTRA: $25 en tu primer depósito de $200+
[CTA: Configurar ahora]

Opción 2: Transferir desde otro banco
→ Conecta tu banco en 1 minuto
→ Fondos disponibles en 1-3 días
[CTA: Conectar banco]

Opción 3: Depositar efectivo
→ Deposita en Walmart, CVS, Walgreens
→ Hasta $500, sin comisiones
[CTA: Ver ubicaciones cerca]

¿Prefieres hacerlo por la app? [Abrir app]

Saludos,
Ana

P.S. El 85% de nuestros clientes activos usan Depósito Directo. ¿Por qué? Porque es automático y ganas $25 💵
```

**Analytics**:
```javascript
analytics.track('email_sent', {
  email_id: 'funding_reminder',
  user_segment: 'unfunded',
  ppc_count: 1,
  hours_since_signup: 12
});
```

---

### **EMAIL 3: DD Setup Tutorial** (T+24 hours, IF DD not set up)
**Trigger**: Direct Deposit not configured after 24 hours
**Subject** (ES): Tutorial: Cómo configurar Depósito Directo en 2 minutos
**Subject** (EN): Tutorial: Set up Direct Deposit in 2 minutes

**Body** (Spanish):
```
Hola [FirstName],

El Depósito Directo es la forma #1 que nuestros clientes usan para fondear sus cuentas. ¿Por qué?

✅ Tu salario llega 2 días ANTES
✅ No tienes que acordarte de transferir dinero
✅ BONO: $25 en tu primer depósito de $200+

---

TUTORIAL: 2 MINUTOS PARA CONFIGURAR

Paso 1: Abre la app MyBambu
Paso 2: Toca "Depósito Directo"
Paso 3: Sigue las instrucciones (nosotros generamos el formulario por ti)
Paso 4: Envía el formulario a tu empleador
¡Listo! Tu próximo salario llegará a MyBambu.

[CTA: Configurar ahora]

---

VIDEO TUTORIAL (1:47 minutos)
[Thumbnail: screenshot del flujo]
[Link a YouTube video]

---

¿Tienes preguntas? Estas son las más comunes:

Q: ¿Mi empleador acepta esto?
A: Sí. Más del 95% de empleadores en USA aceptan depósito directo.

Q: ¿Cuánto tarda en procesarse?
A: Usualmente 1-2 períodos de pago (2-4 semanas).

Q: ¿Puedo dividir mi salario entre MyBambu y otro banco?
A: ¡Sí! Puedes configurar depósito parcial (ej: 50% a MyBambu, 50% a otro banco).

Q: ¿Qué pasa si me equivoco?
A: No problem. Puedes cambiar o cancelar cuando quieras con tu empleador.

[CTA: Tengo más preguntas - Chat con nosotros]

Saludos,
Ana

P.S. Clientes con DD activo ganan 3× más en recompensas. ¿Por qué? Porque usan su cuenta más 🚀
```

---

### **EMAIL 4: Card Activation** (T+5-7 days, when card delivered)
**Trigger**: Card delivered (tracking shows "delivered")
**Subject** (ES): 🎉 ¡Tu tarjeta MyBambu llegó! Actívala en 30 segundos
**Subject** (EN): 🎉 Your MyBambu card arrived! Activate in 30 seconds

**Body** (Spanish):
```
Hola [FirstName],

¡Tu tarjeta de débito MyBambu llegó! 📬

Actívala ahora para empezar a usarla:

Opción 1: Desde la app (30 segundos)
1. Abre la app MyBambu
2. Toca "Activar tarjeta"
3. Ingresa los últimos 4 dígitos: [LastFourCardNumber]
¡Listo! Ya puedes usarla.

[CTA: Abrir app]

Opción 2: Por teléfono
Llama al 1-855-MYBAMBU y sigue las instrucciones.

---

🎁 BONO: GANA $5

Activa tu tarjeta hoy y haz una compra de $5+ antes del [Date+7days] para ganar $5 en tu cuenta.

Condiciones: Compra debe ser con tu tarjeta de débito MyBambu. Bono se acredita en 24-48 horas.

[CTA: Activar ahora]

---

TIP: Usa tu tarjeta MyBambu para TODAS tus compras diarias y gana cashback automático:

🛒 Supermercado: 2% cashback
⛽ Gasolina: 3% cashback
🍕 Restaurantes: 2% cashback
🎬 Entretenimiento: 1% cashback

Saludos,
Ana

P.S. ¿Sabías que puedes añadir tu tarjeta a Apple Pay o Google Pay? Paga con tu teléfono 📱
```

---

### **EMAIL 5: Rewards Education** (T+3 days)
**Trigger**: Rewards activated but 0 points earned
**Subject** (ES): ¿Sabías que puedes ganar $50+ al mes en recompensas? 💰
**Subject** (EN): Did you know you can earn $50+/month in rewards? 💰

**Body** (Spanish):
```
Hola [FirstName],

Tienes el programa de Recompensas Bambu activado, pero aún no has ganado puntos. 😢

La buena noticia: ¡Ganar puntos es súper fácil!

---

5 FORMAS DE GANAR PUNTOS

1. Compras con tu tarjeta 💳
   → 1 punto por cada $1 gastado
   → Ejemplo: Gastas $100 en supermercado = 100 puntos

2. Depósito Directo 💵
   → 500 puntos por cada depósito
   → Ejemplo: Recibes tu salario = 500 puntos

3. Referir amigos 👥
   → 1,000 puntos por cada amigo que abra cuenta
   → Ejemplo: Refieres 3 amigos = 3,000 puntos

4. Pagar servicios ⚡
   → 50 puntos por cada pago (luz, agua, teléfono)
   → Ejemplo: Pagas 3 servicios al mes = 150 puntos

5. Ahorro automático 🏦
   → 100 puntos por cada transferencia a ahorros
   → Ejemplo: Ahorras $50/mes = 100 puntos

TOTAL AL MES: ~2,000 puntos = $20 en premios

---

¿QUÉ PUEDES CANJEAR?

💵 Cash (directo a tu cuenta)
   → 1,000 puntos = $10

🎁 Gift cards (Amazon, Walmart, Target)
   → 1,500 puntos = $15 gift card

📱 Datos móviles (recargas)
   → 500 puntos = $5 recarga

🎮 Premios especiales (AirPods, consolas, etc.)
   → Desde 5,000 puntos

[CTA: Ver todos los premios]

---

EMPIEZA HOY: HAZ UNA COMPRA

Compra algo pequeño con tu tarjeta MyBambu (ej: café, gasolina) y gana tus primeros puntos.

[CTA: Ver mi saldo de puntos]

Saludos,
Ana

P.S. Clientes activos ganan un promedio de $45/mes en recompensas. ¿Quieres ser uno de ellos? 🚀
```

---

### **EMAIL 6: Multi-Product Benefits** (T+7 days, IF PPC < 3)
**Trigger**: User has < 3 products after 7 days
**Subject** (ES): [FirstName], estás dejando dinero sobre la mesa 💸
**Subject** (EN): [FirstName], you're leaving money on the table 💸

**Body** (Spanish):
```
Hola [FirstName],

Veo que solo usas [CurrentPPCCount] producto(s) de MyBambu.

Esto significa que estás perdiendo:
❌ ~$30/mes en bonos
❌ ~$15/mes en cashback
❌ Beneficios exclusivos

---

¿QUÉ ESTÁS DEJANDO DE GANAR?

Si activaras estos productos, ganarías:

💳 Tarjeta de Débito
   → $5 bono de activación
   → 2-3% cashback en compras
   → Estimado: $20/mes

💵 Depósito Directo
   → $25 bono (primer depósito $200+)
   → Salario 2 días antes
   → Sin comisiones de transferencia

🎁 Recompensas Bambu
   → 1,000 puntos de bienvenida = $10
   → ~$15/mes en recompensas
   → Acceso a sorteos exclusivos

📱 Pago de Servicios
   → Sin comisiones
   → 50 puntos por cada pago
   → Recordatorios automáticos

TOTAL: ~$70 en el primer mes, luego ~$45/mes

---

ACTIVA LOS 4 PRODUCTOS HOY

Toma 5 minutos. Vale la pena.

[CTA: Activar productos]

---

COMPARACIÓN: CLIENTES ACTIVOS vs. TÚ

Clientes con 3+ productos (promedio):
✅ Ganan $45/mes en recompensas
✅ Ahorran $120/año en comisiones
✅ Califican para límites de crédito más altos
✅ Acceso prioritario a nuevos productos

Tú (actualmente):
📊 Ganas ~$5/mes
📊 Solo usas [CurrentPPCCount] producto(s)
📊 No calificas para beneficios premium

¿Quieres cambiar esto? [CTA: Sí, activar ahora]

Saludos,
Ana

P.S. Clientes que activan 3+ productos en los primeros 30 días se quedan con MyBambu 6× más tiempo. ¿Por qué? Porque ven el valor real 🎯
```

---

## 📱 SMS Templates

### **SMS 1: Welcome SMS** (T+0 hours)
**Trigger**: Onboarding completed
**Send time**: Immediately

```
Hola [FirstName]! Bienvenido a MyBambu 🌴

Tu cuenta está lista. Gana $10 esta semana:
→ Fondea $10+ = $3
→ Activa tarjeta = $5
→ Primera compra = $2

Ver tareas: [Short link]

Reply STOP to unsubscribe
```

**Character count**: 159 characters (1 SMS)

---

### **SMS 2: Funding Reminder** (T+24 hours, IF not funded)
**Trigger**: Account not funded after 24 hours
**Send time**: 10:00am user's local timezone

```
[FirstName], tu cuenta MyBambu aún no tiene fondos 😢

Fondea con Depósito Directo y recibe tu salario 2 días antes + $25 bono.

Configurar: [Short link]

Reply STOP to unsubscribe
```

**Character count**: 156 characters (1 SMS)

---

### **SMS 3: Card Delivered** (T+5-7 days)
**Trigger**: Card tracking shows "delivered"

```
🎉 Tu tarjeta MyBambu llegó!

Actívala en 30 segundos: [Short link]

Bonus: Actívala hoy + compra $5+ = $5 bono

Reply STOP to unsubscribe
```

**Character count**: 135 characters (1 SMS)

---

### **SMS 4: First Purchase Incentive** (T+1 day after card activation)
**Trigger**: Card activated but no purchases after 24 hours

```
[FirstName], tu tarjeta está activa 💳

Haz tu primera compra de $5+ HOY y gana $5 bono + empieza a ganar cashback.

Caduca en 48 horas ⏰

Reply STOP to unsubscribe
```

**Character count**: 153 characters (1 SMS)

---

### **SMS 5: Rewards Milestone** (Trigger: First 100 points earned)
**Trigger**: User earns 100+ points for first time

```
🎉 Ganaste 100 puntos!

Sigue así. En 900 puntos más, puedes canjear por $10 cash.

Ver premios: [Short link]

Reply STOP to unsubscribe
```

**Character count**: 132 characters (1 SMS)

---

### **SMS 6: Weekly Engagement** (Every Monday, IF PPC < 3)
**Trigger**: Monday 9:00am, IF user has < 3 products
**Send time**: 9:00am user's local timezone

```
Feliz lunes [FirstName]! 🌞

Esta semana, activa 1 producto más y gana $10 extra.

Opciones: [Short link]

Toma 2 minutos. Vale la pena 💰

Reply STOP to unsubscribe
```

**Character count**: 147 characters (1 SMS)

---

## 📊 Push Notification Templates

### **PUSH 1: Task Completed** (Real-time)
**Trigger**: User completes a rewards task
**Send time**: Immediately

```
Title: ¡Ganaste $3! 🎉
Body: Completaste "Fondea tu cuenta". 2 tareas más para tu bono de $10.
Action: Ver tareas
```

---

### **PUSH 2: New Product Recommendation** (T+3 days)
**Trigger**: User has been inactive for 24 hours + has < 3 products
**Send time**: 6:00pm user's local timezone

```
Title: [FirstName], recomendación para ti
Body: Basado en tu actividad, Depósito Directo te ahorraría $15/mes. Configurar en 2 min?
Action: Configurar ahora
```

---

### **PUSH 3: Rewards Expiring** (T+25 days)
**Trigger**: User has unclaimed rewards points + Day 25 of first 30 days
**Send time**: 10:00am user's local timezone

```
Title: ⚠️ Tus puntos expiran en 5 días
Body: Tienes [PointsBalance] puntos sin canjear. Canjéalos antes del [ExpiryDate] o los pierdes.
Action: Canjear ahora
```

---

## 📈 Journey Metrics Dashboard

Track these metrics daily:

| Day | Email Open Rate | SMS CTR | Push CTR | PPC Change | Funding % |
|-----|----------------|---------|----------|------------|-----------|
| 1   | 45%            | 12%     | 18%      | 1.0 → 1.2  | 24%       |
| 3   | 38%            | 10%     | 15%      | 1.2 → 1.5  | 38%       |
| 7   | 32%            | 8%      | 12%      | 1.5 → 2.0  | 52%       |
| 14  | 28%            | 7%      | 10%      | 2.0 → 2.4  | 64%       |
| 30  | 25%            | 6%      | 8%       | 2.4 → 2.8  | 76%       |

**Target by Day 30**:
- PPC: 2.8+ (currently 1.2)
- Funding rate: 76% (currently 24%)
- 3+ products: 55% of users (currently 18%)

---

## 🧪 A/B Test Plan

### Test 1: Incentive Amounts
- **Variant A**: Current amounts ($3, $5, $2)
- **Variant B**: 2× amounts ($6, $10, $4)
- **Hypothesis**: Higher incentives increase task completion but may attract fraud

### Test 2: Email Frequency
- **Variant A**: Current cadence (6 emails in 30 days)
- **Variant B**: Higher frequency (12 emails in 30 days)
- **Hypothesis**: More touchpoints increase PPC but may increase unsubscribes

### Test 3: SMS Timing
- **Variant A**: Mornings (9-11am)
- **Variant B**: Evenings (6-8pm)
- **Hypothesis**: Evening SMS have higher CTR for working adults

---

## ✅ Technical Implementation

### Email Service: SendGrid or Mailgun
- Transactional email API
- Template variables for personalization
- Tracking: opens, clicks, unsubscribes

### SMS Service: Twilio
- Programmable SMS API
- Short link tracking
- STOP keyword handling (auto-unsubscribe)

### Push Notifications: Firebase Cloud Messaging
- iOS + Android support
- Deep linking to specific app screens
- Badge count management

### User Segments in Database:
```sql
CREATE TABLE user_engagement_segments (
  user_id UUID PRIMARY KEY,
  ppc_count INT,
  is_funded BOOLEAN,
  has_dd BOOLEAN,
  has_card BOOLEAN,
  has_rewards BOOLEAN,
  last_activity_at TIMESTAMP,
  created_at TIMESTAMP
);

CREATE INDEX idx_ppc_count ON user_engagement_segments(ppc_count);
CREATE INDEX idx_is_funded ON user_engagement_segments(is_funded);
```

---

## 🚨 Unsubscribe Handling

Users can unsubscribe from:
- **Emails**: "Unsubscribe" link in footer
- **SMS**: Reply "STOP"
- **Push**: Disable in app settings

**Important**: Even if user unsubscribes from marketing, still send:
- Transactional emails (password reset, receipts)
- Security alerts (unusual activity)
- Legal notices (Terms of Service updates)

---

**Questions? Slack: #engagement-sprint or DM @valinfante**
