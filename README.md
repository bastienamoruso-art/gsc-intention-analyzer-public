# 🎯 GSC Intention Analyzer (Version Publique)

Découvrez les micro-intentions cachées dans votre trafic Google Search Console avec l'IA Claude.

> **Version publique** : Utilisez votre propre clé API Anthropic pour garder le contrôle total de vos données et coûts.

## ✨ Fonctionnalités

- ✅ **Classification dynamique** : Découverte automatique des intentions (pas de catégories fixes)
- ✅ **Matrice Position × Intention** : CTR moyen calculé sur VOS données
- ✅ **Patterns linguistiques** : Détection des structures récurrentes
- ✅ **Insights actionnables** : Opportunités, frictions, quick wins
- ✅ **Guide vers analyse manuelle** : Sélection des 5 requêtes stratégiques

## 🚀 Installation en local

### Prérequis

- Node.js 18+ installé
- Une clé API d'un des providers suivants :
  - **Anthropic (Claude)** → [Obtenez-la ici](https://console.anthropic.com/)
  - **OpenAI (GPT)** → [Obtenez-la ici](https://platform.openai.com/api-keys)
  - **Google (Gemini)** → [Obtenez-la ici](https://makersuite.google.com/app/apikey)

### Étapes

1. **Cloner le projet**
```bash
git clone https://github.com/votre-username/gsc-intention-analyzer-public.git
cd gsc-intention-analyzer-public
```

2. **Installer les dépendances**
```bash
npm install
```

3. **Lancer en développement**
```bash
npm run dev
```

4. **Ouvrir http://localhost:3000**

5. **Choisir votre provider IA** et **entrer votre clé API** dans l'interface (elle sera sauvegardée dans votre navigateur)

## 📦 Déploiement sur Vercel (RECOMMANDÉ)

### Pourquoi Vercel ?
- ✅ Hébergement gratuit
- ✅ HTTPS automatique
- ✅ Déploiement en 2 minutes
- ✅ Gestion sécurisée des variables d'environnement
- ✅ Aucune configuration serveur

### Étapes de déploiement

#### 1. Créer un compte Vercel

Allez sur https://vercel.com et créez un compte (gratuit).

#### 2. Initialiser Git (si pas déjà fait)

```bash
cd /Users/Bastien/gsc-intention-analyzer
git init
git add .
git commit -m "Initial commit: GSC Intention Analyzer"
```

#### 3. Option A : Déployer via GitHub (RECOMMANDÉ)

1. Créez un nouveau repo sur GitHub
2. Poussez votre code :
```bash
git remote add origin https://github.com/VOTRE-USERNAME/gsc-intention-analyzer.git
git branch -M main
git push -u origin main
```

3. Sur Vercel :
   - Cliquez sur "New Project"
   - Importez votre repo GitHub
   - Vercel détectera automatiquement Next.js

4. Cliquez sur "Deploy" 🚀

**Note** : Aucune variable d'environnement nécessaire ! Les utilisateurs entrent leur propre clé API dans l'interface.

#### 3. Option B : Déployer via Vercel CLI

```bash
npm install -g vercel
vercel login
vercel
```

Suivez les instructions.

### 🔒 Sécurité & Confidentialité

**Votre clé API** :
- ✅ Stockée **uniquement dans votre navigateur** (localStorage)
- ✅ Jamais sauvegardée sur un serveur
- ✅ Vous gardez le contrôle total

**Vos données** :
- ✅ Aucune donnée GSC stockée
- ✅ Traitement en temps réel uniquement
- ✅ Code source ouvert et auditable

## 🎯 Utilisation

1. **Préparez votre export GSC**
   - Google Search Console → Performance → Requêtes
   - Exportez en CSV

2. **Uploadez dans l'outil**
   - Choisissez votre provider IA (Anthropic, OpenAI ou Gemini)
   - Entrez votre clé API
   - Entrez votre marque (optionnel)
   - Entrez votre secteur (optionnel)
   - Uploadez le CSV

3. **Analysez**
   - L'outil découvre automatiquement les intentions
   - Génère la matrice Position × Intention
   - Détecte les patterns linguistiques

4. **Passez à l'analyse manuelle**
   - Sélectionnez les 5 requêtes recommandées
   - Tapez-les dans Google
   - Analysez les SERP manuellement (comme dans la méthodologie Newsletter)

## 📊 Structure du projet

```
gsc-intention-analyzer/
├── app/
│   ├── api/
│   │   └── analyze/
│   │       └── route.ts          # API Route sécurisée (appel Claude)
│   ├── layout.tsx                # Layout principal
│   └── page.tsx                  # Page d'accueil
├── components/
│   └── GSCIntentionAnalyzer.tsx  # Composant React principal
├── .env.local.example            # Template variables d'environnement
├── package.json
├── tsconfig.json
└── README.md
```

## 🔧 Architecture technique

### Frontend (React/Next.js)
- Upload CSV avec parsing automatique
- Interface en 2 étapes (Upload → Résultats)
- Visualisations avec Recharts (PieChart, Matrice)

### Backend (Next.js API Routes)
- Endpoint `/api/analyze` pour appels IA multi-providers
- Support de 3 modèles :
  - **Claude Sonnet 4.5** (Anthropic)
  - **GPT-4o** (OpenAI)
  - **Gemini 2.0 Flash Exp** (Google)
- Prompt optimisé pour découverte dynamique d'intentions

### Sécurité
- Clé API stockée uniquement dans le navigateur de l'utilisateur (localStorage)
- Validation des données d'entrée côté serveur
- Validation du format de clé API par provider
- Pas de stockage de données utilisateur
- Code 100% open-source et auditable

## 🐛 Bugs corrigés (par rapport à la version initiale)

✅ **Clé API manquante** : Maintenant dans variables d'environnement
✅ **CORS client-side** : API Routes Next.js côté serveur
✅ **Modèle invalide** : Utilise `claude-3-5-sonnet-20241022`
✅ **Catégories fixes** : Classification dynamique
✅ **Pas de matrice CTR** : Matrice Position × Intention implémentée
✅ **Parsing CSV fragile** : Gère tous formats d'export GSC

## 📚 Méthodologie

Cet outil automatise la **classification et la génération de matrice** (2 min).

L'**analyse manuelle des SERP** (1h30) reste nécessaire pour :
- Comprendre les contenus qui rankent
- Identifier les formats gagnants
- Affiner la stratégie de contenu

Voir les newsletters fournies pour la méthodologie complète.

## 💡 Roadmap (optionnel)

- [ ] Export des résultats en PDF/CSV
- [ ] Comparaison historique entre exports
- [ ] Rate limiting pour usage public
- [ ] Authentification utilisateur
- [ ] Dashboard multi-projets

## 📝 License

Usage personnel et commercial autorisé.

## 🤝 Support

Pour toute question, ouvrez une issue sur le repo GitHub.

---

**Made with ❤️ for SEO professionals**
