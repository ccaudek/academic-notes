
# ESEMPI PRATICI - Nuove funzionalità grafiche

Da usare nei capitoli dopo aver caricato _common.R

## 1. PALETTE QUALITATIVA per categorie multiple


## PRIMA (tutti grigi, confuso)
library(ggplot2)

# Dati esempio: punteggi per 4 gruppi di trattamento
dati_gruppi <- data.frame(
  gruppo = rep(c("Controllo", "CBT", "Farmaco", "Combinato"), each = 30),
  punteggio = c(
    rnorm(30, mean = 45, sd = 10),  # Controllo
    rnorm(30, mean = 38, sd = 9),   # CBT
    rnorm(30, mean = 35, sd = 8),   # Farmaco
    rnorm(30, mean = 28, sd = 7)    # Combinato
  )
)

# PRIMA: tutto grigio
ggplot(dati_gruppi, aes(x = gruppo, y = punteggio, fill = gruppo)) +
  geom_boxplot() +
  labs(title = "PRIMA: Difficile distinguere i gruppi")

## DOPO (colorato e accessibile)
ggplot(dati_gruppi, aes(x = gruppo, y = punteggio, fill = gruppo)) +
  geom_boxplot() +
  scale_fill_qualitative() +  # ← NUOVA PALETTE
  labs(title = "DOPO: Gruppi ben distinguibili (colorblind-safe)") +
  legenda_nascosta  # Il colore è già sull'asse x


# ============================================================================
# 2. PALETTE BINARIA per confronti pre/post o controllo/trattamento
# ============================================================================

## Dati pre-post trattamento
dati_prepost <- data.frame(
  id = rep(1:25, 2),
  tempo = rep(c("Pre", "Post"), each = 25),
  ansia = c(
    rnorm(25, mean = 45, sd = 8),   # Pre
    rnorm(25, mean = 32, sd = 7)    # Post
  )
)

# DOPO: colori appropriati per pre/post
ggplot(dati_prepost, aes(x = tempo, y = ansia, fill = tempo)) +
  geom_violin(alpha = 0.6) +
  geom_jitter(width = 0.1, alpha = 0.4) +
  scale_fill_binary() +  # ← GRIGIO per pre, PRIMARY per post
  labs(
    title = "Riduzione ansia pre-post trattamento",
    x = "Momento",
    y = "Punteggio ansia (BDI-II)"
  ) +
  legenda_nascosta


# ============================================================================
# 3. HELPER: Prior vs Posterior
# ============================================================================

## Simulazione aggiornamento bayesiano
set.seed(123)

# Prior vago: Beta(2, 2)
prior_samples <- rbeta(10000, 2, 2)

# Dati osservati: 15 successi su 20 prove
# Posterior: Beta(2+15, 2+5) = Beta(17, 7)
posterior_samples <- rbeta(10000, 17, 7)

# USO DIRETTO della funzione helper
plot_prior_posterior(
  prior_samples = prior_samples,
  posterior_samples = posterior_samples,
  parameter_name = "θ (probabilità successo)",
  title = "Aggiornamento: da prior vago a posterior informato"
)


# ============================================================================
# 4. HELPER: Intervallo di Credibilità
# ============================================================================

## Distribuzione posteriori per un parametro
posterior <- rnorm(10000, mean = 0.35, sd = 0.08)

plot_credible_interval(
  samples = posterior,
  prob = 0.95,
  parameter_name = "Dimensione effetto (d di Cohen)",
  title = "Stima della dimensione effetto con IC 95%"
)


# ============================================================================
# 5. HELPER: Istogramma + Densità
# ============================================================================

## Distribuzione campionaria
dati_campione <- data.frame(
  valore = rnorm(500, mean = 100, sd = 15)
)

ggplot(dati_campione, aes(x = valore)) +
  geom_hist_density(bins = 30) +  # ← HELPER: istogramma + densità
  labs(
    title = "Distribuzione punteggi QI (n=500)",
    x = "Punteggio QI",
    y = "Densità"
  ) +
  geom_vline_primary(xintercept = 100) +  # Media teorica
  annotate_primary(
    "text", x = 105, y = 0.025,
    label = "Media = 100", hjust = 0
  )


# ============================================================================
# 6. HELPER: QQ Plot per normalità
# ============================================================================

## Test normalità visivo
dati_test <- data.frame(
  normale = rnorm(200, mean = 50, sd = 10),
  t_pesante = rt(200, df = 3) * 10 + 50  # Code pesanti
)

# Normale
plot_qq_normal(
  data = dati_test, 
  var = normale,
  title = "Dati normali: punti sulla linea"
)

# Non normale (code pesanti)
plot_qq_normal(
  data = dati_test, 
  var = t_pesante,
  title = "Dati con code pesanti: deviazione dalla linea"
)


# ============================================================================
# 7. CONFRONTO DISTRIBUZIONI
# ============================================================================

## Confronto Normale vs t di Student
x_range <- seq(-4, 4, length.out = 200)

distribuzioni <- list(
  "Normale(0,1)" = function(x) dnorm(x, mean = 0, sd = 1),
  "t(3)" = function(x) dt(x, df = 3),
  "t(10)" = function(x) dt(x, df = 10)
)

plot_distribution_comparison(
  x_range = x_range,
  distributions_list = distribuzioni,
  title = "Confronto: Normale vs t di Student"
)


# ============================================================================
# 8. GRAFICO COMPLESSO: Convergenza media campionaria (LGN)
# ============================================================================

## Simulazione legge grandi numeri
n_max <- 1000
set.seed(42)
dati <- rnorm(n_max, mean = 5, sd = 2)

convergenza <- data.frame(
  n = 1:n_max,
  media_cumulativa = cumsum(dati) / (1:n_max)
)

ggplot(convergenza, aes(x = n, y = media_cumulativa)) +
  geom_line(color = modern_palette$grey3, linewidth = 0.8) +
  geom_hline_primary(yintercept = 5) +  # Media vera
  annotate_primary(
    "text", x = n_max * 0.8, y = 5.3,
    label = "μ = 5 (valore vero)", size = 4
  ) +
  scale_x_continuous(breaks = seq(0, n_max, 200)) +
  labs(
    title = "Legge dei Grandi Numeri: convergenza al valore vero",
    x = "Dimensione campione (n)",
    y = "Media campionaria cumulativa",
    caption = "La media campionaria converge a μ = 5 all'aumentare di n"
  ) +
  nessuna_griglia +  # Solo asse, no griglia
  theme(panel.border = element_rect(fill = NA, color = modern_palette$border))


# ============================================================================
# 9. FACET con palette qualitativa
# ============================================================================

## Confronto trattamenti per gravità iniziale
dati_facet <- expand.grid(
  gravita = c("Lieve", "Moderata", "Grave"),
  trattamento = c("Controllo", "CBT", "Farmaco"),
  replica = 1:20
) |>
  mutate(
    riduzione = case_when(
      trattamento == "Controllo" ~ rnorm(n(), 5, 3),
      trattamento == "CBT" ~ rnorm(n(), 15, 4),
      trattamento == "Farmaco" ~ rnorm(n(), 12, 4)
    ) * case_when(
      gravita == "Lieve" ~ 0.7,
      gravita == "Moderata" ~ 1.0,
      gravita == "Grave" ~ 1.3
    )
  )

ggplot(dati_facet, aes(x = trattamento, y = riduzione, fill = trattamento)) +
  geom_boxplot() +
  facet_wrap(~ gravita) +
  scale_fill_qualitative() +  # ← Colori consistenti tra facet
  labs(
    title = "Efficacia trattamenti per gravità sintomi",
    x = "Tipo di trattamento",
    y = "Riduzione sintomi (punti)",
    fill = "Trattamento"
  ) +
  legenda_in_alto +
  theme(
    strip.background = element_rect(
      fill = modern_palette$off_white,
      color = modern_palette$border
    )
  )


# ============================================================================
# 10. CHUNK OPTIONS per grafici pesanti
# ============================================================================

## Per simulazioni computazionalmente intensive, usare:

#| cache: true
#| cache.vars: !expr c("risultati_simulazione")
#| fig-cap: "Risultati di 10000 simulazioni Monte Carlo"

# risultati_simulazione <- replicate(10000, {
#   # ... codice pesante
# })
# 
# ggplot(...) + ...

# Il chunk viene rieseguito solo se cambia il codice, 
# risparmiando tempo durante lo sviluppo


# ============================================================================
# BEST PRACTICES
# ============================================================================

## 1. Usa scale_fill_qualitative() per categorie > 2
## 2. Usa scale_fill_binary() per confronti pre/post, controllo/trattamento
## 3. Usa helper plot_* per pattern comuni (prior/posterior, IC, QQ)
## 4. Usa geom_*_primary() per annotazioni importanti
## 5. Cache i chunk pesanti con #| cache: true
## 6. Aggiungi sempre fig-cap e fig-alt per accessibilità
