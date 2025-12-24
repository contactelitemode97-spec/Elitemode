# Elitemode
elitemode/
├─ pages/
│   ├─ index.js
├─ components/
│   ├─ ui/
│       ├─ button.js
│       ├─ card.js
├─ public/
│   ├─ logo.png
├─ styles/
│   ├─ globals.css
├─ package.json
├─ README.md
├─ .gitignore
{
  "name": "elitemode",
  "version": "1.0.0",
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start"
  },
  "dependencies": {
    "next": "latest",
    "react": "latest",
    "react-dom": "latest"
  }
}import { useState } from "react";

export default function Boutique() {
  const produitsInit = [
    { id: 1, nom: "Sneakers Luxe", prix: 79.9, categorie: "Chaussures", image: "/sneakers-luxe.jpg" },
    { id: 2, nom: "Baskets Street", prix: 69.9, categorie: "Chaussures", image: "/baskets-street.jpg" },
    { id: 3, nom: "T-shirt Premium", prix: 29.9, categorie: "Vêtements", image: "/tshirt-premium.jpg" },
    { id: 4, nom: "Sweat Élite", prix: 49.9, categorie: "Vêtements", image: "/sweat-elite.jpg" }
  ];

  const [panier, setPanier] = useState([]);

  const ajouterAuPanier = (produit) => {
    setPanier([...panier, produit]);
  };

  const total = panier.reduce((s, p) => s + p.prix, 0);

  const commanderWhatsApp = () => {
    const message = panier.map((p) => `- ${p.nom} : ${p.prix}€`).join("\n");
    const url = `https://wa.me/590690865477?text=${encodeURIComponent(
      `Bonjour Élite Mode, je souhaite commander :\n${message}\nTotal : ${total}€`
    )}`;
    window.open(url, "_blank");
  };

  return (
    <div className="container">
      <header>
        <h1>ÉLITE MODE</h1>
        <p>Chaussures & Vêtements Premium – Livraison France & DOM-TOM</p>
      </header>
      <main className="grid">
        {produitsInit.map((p) => (
          <div key={p.id} className="card">
            <img src={p.image} alt={p.nom} />
            <h3>{p.nom}</h3>
            <p>{p.categorie}</p>
            <p>{p.prix} €</p>
            <button onClick={() => ajouterAuPanier(p)}>Ajouter au panier</button>
          </div>
        ))}
      </main>
      <footer>
        <h2>Panier : {panier.length} article(s)</h2>
        <p>Total : {total.toFixed(2)} €</p>
        <button onClick={commanderWhatsApp} disabled={panier.length === 0}>
          Commander via WhatsApp
        </button>
        <p>© 2025 ÉLITE MODE – Livraison France & DOM-TOM</p>
      </footer>
    </div>
  );
}body {
  font-family: Arial, sans-serif;
  background: #111;
  color: #fff;
  padding: 20px;
}
.container {
  max-width: 1000px;
  margin: auto;
}
.grid {
  display: grid;
  gap: 20px;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
}
.card {
  background: #222;
  padding: 15px;
  border-radius: 12px;
  text-align: center;
}
.card img {
  max-height: 150px;
  object-fit: contain;
}
button {
  background: #f5a524;
  border: none;
  padding: 10px;
  border-radius: 8px;
  cursor: pointer;
  margin-top: 10px;
}
button:disabled {
  background: #666;
}
footer {
  margin-top: 30px;
  text-align: center;
}node_modules/
.next/
