---
title: AI Task Legal Summarization (Italian)
keywords: documentation
last_updated: December 1st, 2021
tags: [getting-started]
sidebar: mydoc_sidebar
layout: doc
---

The Legal Summarization (Italian) Task is a workflow that generates automatically summaries for legal documents using proprietarly AI-driven NLP summarization model. 
Get in touch with the Askdata team if you want to bind a custom model.


# About the task #

The workflow requires as input:
- **dataset** (*mandatory*)
- **column_name**: name of a column of the given dataset (*mandatory*)
- **output_column_name**: name of the target column where summaries will be stored (*optional*)

The workflow returns as output a new dataset with the selected **column_name** and the **output_column_name** if specifies, **Summarized Text** otherwise.

# Example of usage #

Given the dataset below with some italian legal documents and as **column_name** the *Legal Content* column:

|ID|Legal Content|
|--|-------------|
|0 |Con ordinanza n. 36451 del 24 novembre 2021, la Corte di Cassazione è intervenuta in merito ai criteri di scelta dei lavoratori da licenziare in una procedura di licenziamento collettivo, affermando che le parti possono legittimamente differire da quelli proposti dal legislatore. Nel caso specifico le parti sociali avevano individuato i lavoratori da licenziare unicamente tra quelli presenti all’interno della sola unità produttiva da dismettere. I giudici della Suprema Corte hanno confermato che nell’ambito di un licenziamento collettivo è legittima l’adozione concordata tra le parti sociali di criteri di scelta dei lavoratori da licenziare anche difformi da quelli legali, purché rispondenti a requisiti di obiettività e razionalità. Inoltre è del pari legittima la scelta di escludere dalla comparazione i lavoratori di equivalente professionalità che siano però addetti ad unità produttive non soppresse dislocate sul territorio nazionale in quanto la circostanza, da accertarsi in concreto e nello specifico verificata, che il mantenimento in servizio dei dipendenti appartenenti all’unità soppressa esigerebbe il loro trasferimento in altra sede, con aggravio di costi per l’azienda e interferenza sull’assetto organizzativo.|

The default output, thus without setting **output_column_name**, is:

|ID|Legal Content|Summarized Text|
|--|-|-|
|0 |Con ordinanza n. 36451 del 24 novembre 2021, la Corte di Cassazione è intervenuta in merito ai criteri di scelta dei lavoratori da licenziare in una procedura di licenziamento collettivo, affermando che le parti possono legittimamente differire da quelli proposti dal legislatore. Nel caso specifico le parti sociali avevano individuato i lavoratori da licenziare unicamente tra quelli presenti all’interno della sola unità produttiva da dismettere. I giudici della Suprema Corte hanno confermato che nell’ambito di un licenziamento collettivo è legittima l’adozione concordata tra le parti sociali di criteri di scelta dei lavoratori da licenziare anche difformi da quelli legali, purché rispondenti a requisiti di obiettività e razionalità. Inoltre è del pari legittima la scelta di escludere dalla comparazione i lavoratori di equivalente professionalità che siano però addetti ad unità produttive non soppresse dislocate sul territorio nazionale in quanto la circostanza, da accertarsi in concreto e nello specifico verificata, che il mantenimento in servizio dei dipendenti appartenenti all’unità soppressa esigerebbe il loro trasferimento in altra sede, con aggravio di costi per l’azienda e interferenza sull’assetto organizzativo.|Sull'illegittimità di un licenziamento collettivo per i lavoratori da licenziare in una procedura di licenziamento collettivi ai sensi dell'art. 36451 del 24 novembre 1921, la corte di cassazione è intervenuta in merito - enunciando "i criteri di scelta dei lavoratori" da dismettere in un procedimento di licenziamenti collettivi, affermando che le parti possono legittimamente differire da quelli proposti dal legislatore. nell'ambito di una fattispecie verificata, da accertarsi in concreto accertato, che la permanenza in servizio dei dipendenti appartenenti all'unità soppressa esigerebbe conseguentemente o verrebbe snaturata (con aggravio di costi per la impresa ) anziché compromettere gravemente taluni costi sostenuti per gli enti aderenti all’unità produttiva.|

Otherwise, setting **output_column_name** as *Summary*, we have:

|ID|Legal Content|Summary|
|--|-|-|
|0 |Con ordinanza n. 36451 del 24 novembre 2021, la Corte di Cassazione è intervenuta in merito ai criteri di scelta dei lavoratori da licenziare in una procedura di licenziamento collettivo, affermando che le parti possono legittimamente differire da quelli proposti dal legislatore. Nel caso specifico le parti sociali avevano individuato i lavoratori da licenziare unicamente tra quelli presenti all’interno della sola unità produttiva da dismettere. I giudici della Suprema Corte hanno confermato che nell’ambito di un licenziamento collettivo è legittima l’adozione concordata tra le parti sociali di criteri di scelta dei lavoratori da licenziare anche difformi da quelli legali, purché rispondenti a requisiti di obiettività e razionalità. Inoltre è del pari legittima la scelta di escludere dalla comparazione i lavoratori di equivalente professionalità che siano però addetti ad unità produttive non soppresse dislocate sul territorio nazionale in quanto la circostanza, da accertarsi in concreto e nello specifico verificata, che il mantenimento in servizio dei dipendenti appartenenti all’unità soppressa esigerebbe il loro trasferimento in altra sede, con aggravio di costi per l’azienda e interferenza sull’assetto organizzativo.|Sull'illegittimità di un licenziamento collettivo per i lavoratori da licenziare in una procedura di licenziamento collettivi ai sensi dell'art. 36451 del 24 novembre 1921, la corte di cassazione è intervenuta in merito - enunciando "i criteri di scelta dei lavoratori" da dismettere in un procedimento di licenziamenti collettivi, affermando che le parti possono legittimamente differire da quelli proposti dal legislatore. nell'ambito di una fattispecie verificata, da accertarsi in concreto accertato, che la permanenza in servizio dei dipendenti appartenenti all'unità soppressa esigerebbe conseguentemente o verrebbe snaturata (con aggravio di costi per la impresa ) anziché compromettere gravemente taluni costi sostenuti per gli enti aderenti all’unità produttiva.|


{% include links.html %}
