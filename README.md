# Property Due Diligence Checker

A small Express app for recording facts about a property, such as tax trend, permits, flood risk, and code violations, and getting back a list of risk flags. It is for home buyers keeping notes on properties they are considering.

## Features

- Record a property with address, tax trend, permit status, flood risk, and violation count
- Flags flood risk when the value is above 0.3
- Flags code violations and missing permits
- Saves properties to a local `data.json` file

## Getting started

Requires Node.js.

```bash
npm install
npm start
```

The server runs on http://localhost:3017. Add a property and list them:

```bash
curl -X POST http://localhost:3017/api/properties \
  -H "Content-Type: application/json" \
  -d '{"address":"12 Oak St","taxHistory":"rising","permits":true,"floodRisk":0.4,"violations":0}'

curl http://localhost:3017/api/properties
```

## How it works

- `server.js` is an Express server with `POST /api/properties` and `GET /api/properties`. POST returns the property with its risk factors; GET returns the 50 most recent.
- All property details are entered by hand. The app does not look up tax, permit, or flood records.
- Properties are stored in `data.json` in the project folder, which is created on first run and ignored by git.
- `index.html` is served at the root URL but is still a generic placeholder form that is not connected to this API. `utils.js` contains helpers that `server.js` does not use yet.

## Status

Prototype. Manual data entry with simple rule-based flags; the web page is not wired up.

## License

MIT, see [LICENSE](LICENSE).
