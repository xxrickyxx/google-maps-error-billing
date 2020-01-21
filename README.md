# google-maps-error-billing
script javascript che risolve il problema maps development purposes only

Questo script elimina la fastidiosa scritta sulla mappa di google maps  

"maps development purposes only"

Questo errore è data dal fatto di non abilitare la fatturazione e quindi per sbloccare bisognerebbe collegare una credi card valida e pagare!!!!

con questo piccolo script tutto si risolve.

Non mi assumo nessuna responsabilità sull'uso del codice pubblicato.
Il mio è costuire del codice a solo scopo di studio.

<script type="text/javascript">
const appendChild = Element.prototype.appendChild;

const urlCatchers = [
  "/AuthenticationService.Authenticate?",
  "/QuotaService.RecordEvent?"
];


Element.prototype.appendChild = function (element) {
  const isGMapScript = element.tagName === 'SCRIPT' && /maps\.googleapis\.com/i.test(element.src);
  const isGMapAccessScript = isGMapScript && urlCatchers.some(url => element.src.includes(url));

  if (!isGMapAccessScript) {
    return appendChild.call(this, element);
  }


  return element;
};
</script>
