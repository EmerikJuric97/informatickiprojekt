<template>
  <div style="background-color: #212f45; justify-content: center">
    <v-container>
      <v-row>
      <v-col>
      <h3 style="color:white">Pomoću ovoga projekta (web aplikacije) možemo vidjeti sve Pokemon karte, njihovo ime, iz kojega su seta i koje godine su izdane.
        Karte se dobijaju pomoću spjanja na api koji se nalazi na <a href="https://dev.pokemontcg.io/">stranici</a> za developere. U aplikaciji je korišten sami poziv
        na api i dohvaćenje podataka s istog te se sve nalazi na početnoj <a href="/">stranici</a>. Api pozivamo pomoću aksiosa te nakon toga pravim v-for u kojem prolazimo  
        kroz sve podatke s apija i ispisujemo ih pomoću {{}}. Također, korištena je paginacija koju dobijamo tako što podijelimo broj 
        karata koji želimo prikazati s ukupnim brojem karata (u ovom apiju je ukupan broj karata totalCount). Uz to imamo pretraživač u kojem unesemo ime karte i 
        ukoliko postoji on nam vraća kartu sa željenim imenom, filter u kojem označujemo koji tip pokemon želimo(vatreni, vodeni, itd.) te nam klikom na željeni tip prikazuje
        pokemona izabranoga tipa. Na kraju imamo dugme pod nazivom dodaj te klikom na njega otvara nam se prozor u kojem se nalazi forma koja je napisana u zasebnu komponentu
        te je uključena u sami pogled i klikom na dugme dodaj prikazuje se zeleni bar koji nam daje napisanu poruku. 
      </h3>
      </v-col>

      </v-row>
    </v-container>
  </div>
</template>
