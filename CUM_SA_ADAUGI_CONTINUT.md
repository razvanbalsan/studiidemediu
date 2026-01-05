# Ghid: Cum să adaugi conținut nou

## 📢 Adăugare Anunț Nou

### Pași simpli:

1. **Copiază fișierul șablon**
   ```bash
   cp _anunturi/_TEMPLATE.md _anunturi/nume-proiect-2026.md
   ```

2. **Deschide fișierul nou** în editor

3. **Completează informațiile** între `---` (front matter):
   - `title`: Titlul complet al anunțului
   - `date`: Data publicării (format: YYYY-MM-DD)
   - `company`: Numele companiei beneficiare
   - `category`: Tipul anunțului (consultare-publica, audienta-publica, etc.)
   - `excerpt`: Rezumat scurt (1-2 propoziții)
   - `location`: Locația proiectului
   
4. **Completează conținutul** (după al doilea `---`):
   - Descrierea proiectului
   - Documentație disponibilă
   - Informații suplimentare

5. **Șterge toate comentariile** (liniile care încep cu `#`)

6. **Salvează fișierul**

7. **Anunțul apare automat** pe pagina `/anunturi/`

### Exemplu complet:

```markdown
---
title: "Parcul FotovoltaicExample"
date: 2026-01-15
company: "Green Energy SRL"
category: "consultare-publica"
excerpt: "Construirea unui parc fotovoltaic de 50 MW în Comuna Example."
location: "Comuna Example, Județul Cluj"
deadline: "2026-02-15"
consultation_locations:
  - name: "Primăria Example"
    address: "Str. Principală nr. 1, Com. Example"
---

## Descrierea proiectului

Proiectul constă în realizarea unui parc fotovoltaic...
```

---

## 📁 Adăugare Proiect Nou

### Pași simpli:

1. **Copiază fișierul șablon**
   ```bash
   cp _proiecte/_TEMPLATE.md _proiecte/nume-proiect.md
   ```

2. **Deschide fișierul nou** în editor

3. **Completează informațiile** între `---` (front matter):
   - `title`: Numele proiectului
   - `excerpt`: Rezumat scurt
   - `category`: Categoria (energie-regenerabila, infrastructura, etc.)
   - `status`: Statusul proiectului:
     - `in-desfasurare` - pentru proiecte în derulare
     - `in-pregatire` - pentru proiecte planificate
     - `consultare-publica` - pentru proiecte în consultare
     - **Lasă gol** pentru proiecte finalizate (apar doar în portofoliu)
   - `location`: Locația (opțional)

4. **Completează conținutul** (după al doilea `---`):
   - Despre proiect
   - Obiective
   - Servicii oferite
   - Starea proiectului

5. **Șterge toate comentariile** (liniile care încep cu `#`)

6. **Salvează fișierul**

7. **Proiectul apare automat**:
   - Dacă are `status`: în secțiunea "Proiecte curente"
   - Dacă NU are `status`: doar în portofoliu

### Exemplu complet:

```markdown
---
title: "Monitorizare Biodiversitate Parc Natural"
excerpt: "Studiu de monitorizare a faunei și florei pe o suprafață de 1000 ha."
category: "biodiversitate"
status: "in-desfasurare"
location: "Parc Natural Example, Județul Alba"
---

## Despre proiect

Proiectul constă în monitorizarea anuală a biodiversității...

## Obiective

- Inventarierea speciilor de păsări
- Evaluarea stării de conservare
- Recomandări de management
```

---

## 🎨 Categorii disponibile

### Pentru Anunțuri:
- `audienta-publica` - Audiență publică
- `consultare-publica` - Consultare publică
- `dezbatere-publica` - Dezbatere publică
- `evaluare-impact` - Evaluare impact de mediu

### Pentru Proiecte:
- `energie-regenerabila` - Energie regenerabilă
- `infrastructura` - Infrastructură de transport
- `biodiversitate` - Biodiversitate și arii protejate
- `dezvoltare-urbana` - Dezvoltare urbană
- `industrie` - Industrie și exploatări
- `cercetare` - Cercetare și inovare

---

## 🚀 Build și Preview

După ce adaugi conținut nou:

```bash
# Pornește serverul local
bundle exec jekyll serve

# Vizitează în browser
http://localhost:4000
```

---

## 📝 Tips & Tricks

### Date și formatare:
- Datele trebuie să fie în format `YYYY-MM-DD` (ex: 2026-01-15)
- Pentru liste în YAML folosește `-` (liniuță)
- Pentru text multi-linie folosește `>` sau `|`

### Front matter opțional:
- Orice câmp marcat "OPȚIONAL" poate fi omis
- Dacă nu ai informații, pur și simplu nu include acel câmp
- Câmpurile obligatorii TREBUIE completate

### Naming conventions:
- Nume fișiere: lowercase, cu cratimă (ex: `parc-eolian-2026.md`)
- Fără spații, fără caractere speciale
- Folosește nume descriptive

### Markdown în conținut:
- `## Titlu` - Heading nivel 2
- `### Subtitlu` - Heading nivel 3
- `**bold**` - Text bold
- `*italic*` - Text italic
- `[link text](url)` - Link
- `- item` - Listă cu bullet points

---

## ❓ Întrebări frecvente

**Q: Cum fac un proiect să apară în "Proiecte curente"?**
A: Adaugă un câmp `status` cu valoarea `in-desfasurare`, `in-pregatire` sau `consultare-publica`.

**Q: Cum fac un proiect să apară doar în portofoliu?**
A: Nu include câmpul `status` sau lasă-l complet gol.

**Q: Pot folosi HTML în conținut?**
A: Da, poți mixa Markdown cu HTML, dar Markdown este mai ușor.

**Q: Cum adaug mai multe locații de consultare?**
A: Folosește formatul listă YAML:
```yaml
consultation_locations:
  - name: "Locație 1"
    address: "Adresa 1"
  - name: "Locație 2"
    address: "Adresa 2"
```

**Q: Unde apar anunțurile după publicare?**
A: Automat pe pagina `/anunturi/` în ordinea datei (cele mai noi sus).

---

## 📧 Suport

Pentru probleme sau întrebări, consultați documentația Jekyll sau contactați administratorul site-ului.
