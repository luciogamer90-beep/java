 (cd "$(git rev-parse --show-toplevel)" && git apply --3way <<'EOF' 
diff --git a/GUIDA_SEMPLICE_IT.md b/GUIDA_SEMPLICE_IT.md
new file mode 100644
index 0000000000000000000000000000000000000000..45cd7d512b6589c4abd79659164c84b59bfe710c
--- /dev/null
+++ b/GUIDA_SEMPLICE_IT.md
@@ -0,0 +1,209 @@
+# Guida super-semplice (passo passo) – se non hai mai fatto mod
+
+Ti guido proprio da zero. Fai i passaggi in ordine.
+
+## Obiettivo finale
+
+Arrivare ad avere questo file:
+
+```text
+build/libs/playerbookmod-1.0.0.jar
+```
+
+Poi copiarlo nella cartella `mods` di Minecraft (con Fabric).
+
+---
+
+## 1) Controlla Java 21 nel terminale (importantissimo)
+
+Hai detto che hai installato Java 21 ma il terminale non lo vede: succede spesso.
+
+### Windows
+
+Apri **Prompt dei comandi** (tasto Windows -> scrivi `cmd`) e lancia:
+
+```bat
+java -version
+where java
+```
+
+Cosa devi vedere:
+- `java version "21..."` oppure `openjdk version "21..."`
+
+Se NON vedi 21:
+1. Riavvia il PC (o almeno chiudi e riapri terminale/IntelliJ).
+2. Reinstalla JDK 21 (Temurin/Oracle).
+3. Imposta `JAVA_HOME` a JDK 21 e aggiungi `%JAVA_HOME%\bin` al `Path`.
+4. Riprova `java -version`.
+
+### macOS / Linux
+
+Nel terminale:
+
+```bash
+java -version
+which java
+```
+
+Devi vedere versione 21.
+
+---
+
+## 2) NON creare un progetto vuoto in IntelliJ
+
+Errore comune: fare “New Project” e poi non trovare i file.
+
+Tu devi aprire **la cartella già pronta della mod**.
+
+In IntelliJ:
+1. `File` -> `Open...`
+2. Seleziona la cartella del progetto (quella che contiene `build.gradle`).
+3. Premi `Open as Project`.
+4. Aspetta il caricamento Gradle (in basso a destra di solito).
+
+Se non sai dov’è la cartella:
+- chiedi a chi ti ha inviato i file dove li ha salvati
+- oppure cercala dal file manager cercando `build.gradle`.
+
+---
+
+## 3) Verifica di essere nella cartella giusta
+
+Nel terminale di IntelliJ (tab **Terminal**) esegui:
+
+```bash
+pwd
+```
+
+Se sei su Windows PowerShell:
+
+```powershell
+Get-Location
+```
+
+Devi essere nella cartella del progetto, cioè dove ci sono:
+- `build.gradle`
+- `settings.gradle`
+- cartella `src`
+
+Controlla con:
+
+```bash
+ls
+```
+
+(Windows PowerShell: `dir`)
+
+---
+
+## 4) Compila la mod
+
+Nel terminale, dentro la cartella progetto:
+
+```bash
+gradle build
+```
+
+Se la compilazione va bene, compare `BUILD SUCCESSFUL`.
+
+Il jar sarà qui:
+
+```text
+build/libs/playerbookmod-1.0.0.jar
+```
+
+---
+
+## 5) Installa Fabric (una volta sola)
+
+1. Scarica e installa **Fabric Loader** per Minecraft **1.21.8**.
+2. Avvia almeno una volta il launcher Minecraft con profilo Fabric.
+
+---
+
+## 6) Trova la cartella `mods` di Minecraft
+
+### Windows
+
+Percorso tipico:
+
+```text
+C:\Users\<TUO_UTENTE>\AppData\Roaming\.minecraft\mods
+```
+
+Metodo rapido:
+1. Premi `Win + R`
+2. Scrivi `%appdata%\.minecraft`
+3. Invio
+4. Entra in `mods` (se non c’è, creala)
+
+### macOS
+
+```text
+~/Library/Application Support/minecraft/mods
+```
+
+### Linux
+
+```text
+~/.minecraft/mods
+```
+
+---
+
+## 7) Copia i file giusti in `mods`
+
+Dentro `mods` metti:
+1. `playerbookmod-1.0.0.jar`
+2. `fabric-api` per Minecraft 1.21.8
+
+Senza Fabric API spesso la mod non parte.
+
+---
+
+## 8) Avvio e test in gioco
+
+1. Avvia Minecraft con profilo **Fabric 1.21.8**.
+2. Entra in un server multiplayer.
+3. Metti in una cassa dei **libri firmati** (`Written Book`).
+4. Ogni libro deve avere come **titolo** il nome del giocatore.
+5. Apri la cassa:
+   - slot giallo = giocatore online
+   - no evidenziazione = offline
+6. Tooltip libro:
+   - arancione = online
+   - bianco = offline
+
+---
+
+## Problemi frequenti (soluzioni rapide)
+
+### A) `java -version` non mostra 21
+- Java 21 non è nel PATH
+- terminale aperto prima dell’installazione
+- soluzione: riapri terminale/PC e imposta `JAVA_HOME` + `Path`
+
+### B) `gradle` non riconosciuto
+Se vedi comando non trovato, prova da IntelliJ (terminale integrato) oppure installa Gradle.
+
+### C) Non trovi `build.gradle`
+Hai aperto la cartella sbagliata in IntelliJ.
+Devi aprire la cartella radice del progetto mod.
+
+### D) Minecraft crasha all’avvio
+Controlla:
+- versione Minecraft = 1.21.8
+- Fabric Loader installato
+- Fabric API presente in `mods`
+- jar della mod copiato nella `mods` giusta
+
+---
+
+## Mini-checklist finale
+
+- [ ] `java -version` mostra 21
+- [ ] hai aperto la cartella giusta in IntelliJ (`build.gradle` visibile)
+- [ ] `gradle build` termina con successo
+- [ ] esiste `build/libs/playerbookmod-1.0.0.jar`
+- [ ] file copiati in `.minecraft/mods`
+- [ ] avvio con profilo Fabric 1.21.8
diff --git a/LICENSE b/LICENSE
new file mode 100644
index 0000000000000000000000000000000000000000..14fac913ccf80234b1848540089a3bbcb6e5283d
--- /dev/null
+++ b/LICENSE
@@ -0,0 +1,21 @@
+MIT License
+
+Copyright (c) 2026
+
+Permission is hereby granted, free of charge, to any person obtaining a copy
+of this software and associated documentation files (the "Software"), to deal
+in the Software without restriction, including without limitation the rights
+to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
+copies of the Software, and to permit persons to whom the Software is
+furnished to do so, subject to the following conditions:
+
+The above copyright notice and this permission notice shall be included in all
+copies or substantial portions of the Software.
+
+THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
+IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
+FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
+AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
+LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
+OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
+SOFTWARE.
diff --git a/README.md b/README.md
new file mode 100644
index 0000000000000000000000000000000000000000..c02c6672421fc2ac23969a0447953feaa71a7543
--- /dev/null
+++ b/README.md
@@ -0,0 +1,69 @@
+# Player Book Highlighter (Fabric 1.21.8)
+
+Mod Fabric per Minecraft **1.21.8** che evidenzia i libri firmati nelle casse se il giocatore indicato dal titolo è online.
+
+> Se parti da zero e non sai usare IntelliJ/terminale, segui questa guida dettagliata: **[GUIDA_SEMPLICE_IT.md](GUIDA_SEMPLICE_IT.md)**.
+
+> Se non sai neanche come usare Codex o cosa sono i file del progetto, parti da qui: **[START_HERE_CODEX_IT.md](START_HERE_CODEX_IT.md)**.
+
+## Cosa fa la mod
+
+- Intercetta l'apertura di una cassa lato client.
+- Ogni `Written Book` nella cassa viene letto come “libro di un giocatore” (nome preso dal **titolo** del libro).
+- Se il giocatore è online sul server, lo slot del libro viene evidenziato in **giallo**.
+- Il titolo del libro resta invariato.
+- Nel tooltip compare una riga aggiuntiva colorata:
+  - **arancione** se online
+  - **bianco** se offline
+
+## Struttura progetto
+
+```text
+com.example.playerbookmod
+├── PlayerBookMod.java                (entrypoint comune)
+├── PlayerBookModClient.java          (eventi client: tooltip + overlay)
+├── BookNameResolver.java             (estrazione nome giocatore dal libro)
+└── mixin
+    └── HandledScreenAccessor.java    (accesso coordinate GUI)
+```
+
+## Build rapido (per chi ha già Java/Gradle)
+
+### Requisiti
+
+- JDK 21
+- Connessione internet per scaricare dipendenze Gradle/Fabric
+
+### Comandi
+
+Linux/macOS:
+
+```bash
+gradle build
+```
+
+Windows:
+
+```bat
+gradle build
+```
+
+### Output
+
+Il file `.jar` della mod viene generato in:
+
+```text
+build/libs/playerbookmod-<version>.jar
+```
+
+## Installazione nel gioco
+
+1. Installa **Fabric Loader 1.21.8** nel launcher Minecraft.
+2. Copia nel folder `mods`:
+   - `playerbookmod-<version>.jar`
+   - `fabric-api` compatibile con 1.21.8
+3. Avvia Minecraft con profilo Fabric.
+
+## Note multiplayer
+
+La verifica online/offline usa la player list ricevuta dal server a cui sei connesso, quindi la mod è utile soprattutto in multiplayer.
diff --git a/START_HERE_CODEX_IT.md b/START_HERE_CODEX_IT.md
new file mode 100644
index 0000000000000000000000000000000000000000..dded52e4c1cd88e812eea0c355b7291bb73047cc
--- /dev/null
+++ b/START_HERE_CODEX_IT.md
@@ -0,0 +1,63 @@
+# START HERE - Se non sai usare Codex (guida 5 minuti)
+
+Se vedi tanti file e non capisci niente: è normale.
+
+## 1) Cosa stai vedendo (in parole semplici)
+
+Questa cartella è un **progetto mod Minecraft**.
+
+I file principali sono:
+
+- `build.gradle` -> dice a Gradle come compilare la mod
+- `gradle.properties` -> versioni (Minecraft, Fabric, ecc.)
+- `settings.gradle` -> nome progetto
+- `src/main/java/...` -> codice principale Java della mod
+- `src/client/java/...` -> codice lato client (tooltip/evidenziazione)
+- `src/main/resources/fabric.mod.json` -> dati identificativi della mod
+- `README.md` -> spiegazione generale
+- `GUIDA_SEMPLICE_IT.md` -> guida installazione/compilazione
+
+Quindi quei “15 file” non sono errori: sono i pezzi normali di una mod.
+
+---
+
+## 2) Come usare Codex senza impazzire
+
+Tu in chat devi scrivere richieste **brevi e precise**, ad esempio:
+
+1. `Spiegami solo i 3 file più importanti.`
+2. `Dimmi esattamente cosa cliccare in IntelliJ, passo passo.`
+3. `Ho questo errore: <incolla errore>. Come lo risolvo?`
+
+Se vuoi, puoi anche chiedere:
+
+- `Spiegamelo come a uno che non ha mai programmato.`
+- `Fammi fare un passo alla volta e aspetta la mia conferma.`
+
+---
+
+## 3) Flusso minimo per te (ordine giusto)
+
+1. Controlla Java 21:
+   - Windows: `java -version` + `where java`
+   - macOS/Linux: `java -version` + `which java`
+2. Apri in IntelliJ la cartella che contiene `build.gradle`.
+3. Nel terminale di IntelliJ lancia: `gradle build`.
+4. Prendi il file jar da `build/libs/`.
+5. Copia il jar in `.minecraft/mods` insieme a Fabric API.
+
+Fine. Questo è tutto il necessario per partire.
+
+---
+
+## 4) Se vuoi, usa questo messaggio già pronto in chat
+
+Copia/incolla e invialo:
+
+```text
+Andiamo passo passo. Sono su Windows.
+Ti mando output di `java -version` e `where java`.
+Poi dimmi SOLO il prossimo click da fare in IntelliJ.
+```
+
+Così ti guido senza saltare niente.
diff --git a/build.gradle b/build.gradle
new file mode 100644
index 0000000000000000000000000000000000000000..71e4e45910f60a3b06e4caa0a440a3cb2f1bf2cd
--- /dev/null
+++ b/build.gradle
@@ -0,0 +1,74 @@
+buildscript {
+    repositories {
+        maven {
+            name = 'Fabric'
+            url = 'https://maven.fabricmc.net/'
+        }
+        mavenCentral()
+        gradlePluginPortal()
+    }
+    dependencies {
+        classpath 'net.fabricmc:fabric-loom:1.8-SNAPSHOT'
+    }
+}
+
+apply plugin: 'fabric-loom'
+apply plugin: 'maven-publish'
+
+version = project.mod_version
+group = project.maven_group
+
+base {
+    archivesName = project.archives_base_name
+}
+
+repositories {
+    mavenCentral()
+    maven {
+        name = 'Fabric'
+        url = 'https://maven.fabricmc.net/'
+    }
+}
+
+dependencies {
+    minecraft "com.mojang:minecraft:${project.minecraft_version}"
+    mappings "net.fabricmc:yarn:${project.yarn_mappings}:v2"
+    modImplementation "net.fabricmc:fabric-loader:${project.loader_version}"
+    modImplementation "net.fabricmc.fabric-api:fabric-api:${project.fabric_version}"
+}
+
+processResources {
+    inputs.property 'version', project.version
+
+    filesMatching('fabric.mod.json') {
+        expand 'version': project.version
+    }
+}
+
+tasks.withType(JavaCompile).configureEach {
+    it.options.release = 21
+}
+
+java {
+    withSourcesJar()
+    sourceCompatibility = JavaVersion.VERSION_21
+    targetCompatibility = JavaVersion.VERSION_21
+}
+
+jar {
+    from('LICENSE') {
+        rename { "${it}_${project.base.archivesName.get()}" }
+    }
+}
+
+publishing {
+    publications {
+        mavenJava(MavenPublication) {
+            from components.java
+        }
+    }
+
+    repositories {
+        // Add repositories here if you want to publish.
+    }
+}
diff --git a/gradle.properties b/gradle.properties
new file mode 100644
index 0000000000000000000000000000000000000000..9136166ebf4063217fc802dbdd9f480884b76e94
--- /dev/null
+++ b/gradle.properties
@@ -0,0 +1,12 @@
+org.gradle.jvmargs=-Xmx2G
+org.gradle.parallel=true
+
+minecraft_version=1.21.8
+yarn_mappings=1.21.8+build.1
+loader_version=0.16.10
+
+mod_version=1.0.0
+maven_group=com.example
+archives_base_name=playerbookmod
+
+fabric_version=0.120.0+1.21.8
diff --git a/settings.gradle b/settings.gradle
new file mode 100644
index 0000000000000000000000000000000000000000..d9e67545100afda6baa4ef0366980ad29f96fd82
--- /dev/null
+++ b/settings.gradle
@@ -0,0 +1,12 @@
+pluginManagement {
+    repositories {
+        maven {
+            name = 'Fabric'
+            url = 'https://maven.fabricmc.net/'
+        }
+        mavenCentral()
+        gradlePluginPortal()
+    }
+}
+
+rootProject.name = 'playerbookmod'
diff --git a/src/client/java/com/example/playerbookmod/PlayerBookModClient.java b/src/client/java/com/example/playerbookmod/PlayerBookModClient.java
new file mode 100644
index 0000000000000000000000000000000000000000..5d0ce615c756605d6063b934b13ca6a5fb650ed6
--- /dev/null
+++ b/src/client/java/com/example/playerbookmod/PlayerBookModClient.java
@@ -0,0 +1,92 @@
+package com.example.playerbookmod;
+
+import com.example.playerbookmod.mixin.HandledScreenAccessor;
+import net.fabricmc.api.ClientModInitializer;
+import net.fabricmc.fabric.api.client.item.v1.ItemTooltipCallback;
+import net.fabricmc.fabric.api.client.screen.v1.ScreenEvents;
+import net.minecraft.client.MinecraftClient;
+import net.minecraft.client.gui.DrawContext;
+import net.minecraft.client.gui.screen.Screen;
+import net.minecraft.client.gui.screen.ingame.HandledScreen;
+import net.minecraft.screen.GenericContainerScreenHandler;
+import net.minecraft.screen.slot.Slot;
+import net.minecraft.text.Text;
+import net.minecraft.util.Formatting;
+
+import java.util.Optional;
+
+/**
+ * Entrypoint client:
+ * - colora il tooltip dei libri giocatore in base allo stato online/offline
+ * - evidenzia in giallo gli slot della cassa con giocatore online
+ */
+public class PlayerBookModClient implements ClientModInitializer {
+    private static final int SLOT_FILL_COLOR = 0x66FFFF00;
+    private static final int SLOT_BORDER_COLOR = 0xCCFFD400;
+
+    @Override
+    public void onInitializeClient() {
+        registerTooltipColoring();
+        registerChestSlotHighlighting();
+
+        PlayerBookMod.LOGGER.info("Player Book Highlighter client inizializzata.");
+    }
+
+    private static void registerTooltipColoring() {
+        ItemTooltipCallback.EVENT.register((stack, tooltipContext, tooltipType, lines) -> {
+            Optional<String> playerNameOpt = BookNameResolver.resolvePlayerName(stack);
+            if (playerNameOpt.isEmpty()) {
+                return;
+            }
+
+            String playerName = playerNameOpt.get();
+            boolean online = isPlayerOnline(playerName);
+            lines.add(Text.translatable("tooltip.playerbookmod.player_status", playerName)
+                    .formatted(online ? Formatting.GOLD : Formatting.WHITE));
+        });
+    }
+
+    private static void registerChestSlotHighlighting() {
+        ScreenEvents.AFTER_RENDER.register((screen, drawContext, mouseX, mouseY, tickDelta) -> {
+            if (!(screen instanceof HandledScreen<?> handledScreen)) {
+                return;
+            }
+            if (!(handledScreen.getScreenHandler() instanceof GenericContainerScreenHandler containerHandler)) {
+                return;
+            }
+
+            int screenX = ((HandledScreenAccessor) handledScreen).playerbookmod$getX();
+            int screenY = ((HandledScreenAccessor) handledScreen).playerbookmod$getY();
+
+            // Solo gli slot della cassa (esclude inventario giocatore in basso)
+            int containerSlotCount = containerHandler.getRows() * 9;
+            for (int i = 0; i < containerSlotCount; i++) {
+                Slot slot = containerHandler.slots.get(i);
+                Optional<String> playerNameOpt = BookNameResolver.resolvePlayerName(slot.getStack());
+                if (playerNameOpt.isEmpty() || !isPlayerOnline(playerNameOpt.get())) {
+                    continue;
+                }
+
+                highlightSlot(drawContext, screenX + slot.x, screenY + slot.y);
+            }
+        });
+    }
+
+    private static boolean isPlayerOnline(String playerName) {
+        MinecraftClient client = MinecraftClient.getInstance();
+        return client.getNetworkHandler() != null && client.getNetworkHandler().getPlayerListEntry(playerName) != null;
+    }
+
+    private static void highlightSlot(DrawContext drawContext, int left, int top) {
+        int right = left + 16;
+        int bottom = top + 16;
+
+        drawContext.fill(left, top, right, bottom, SLOT_FILL_COLOR);
+
+        // Bordo giallo più saturo per far risaltare meglio lo slot.
+        drawContext.fill(left, top, right, top + 1, SLOT_BORDER_COLOR);
+        drawContext.fill(left, bottom - 1, right, bottom, SLOT_BORDER_COLOR);
+        drawContext.fill(left, top, left + 1, bottom, SLOT_BORDER_COLOR);
+        drawContext.fill(right - 1, top, right, bottom, SLOT_BORDER_COLOR);
+    }
+}
diff --git a/src/client/java/com/example/playerbookmod/mixin/HandledScreenAccessor.java b/src/client/java/com/example/playerbookmod/mixin/HandledScreenAccessor.java
new file mode 100644
index 0000000000000000000000000000000000000000..fd0f1269ddc4365d009eb6ec671ef054a09719e1
--- /dev/null
+++ b/src/client/java/com/example/playerbookmod/mixin/HandledScreenAccessor.java
@@ -0,0 +1,17 @@
+package com.example.playerbookmod.mixin;
+
+import net.minecraft.client.gui.screen.ingame.HandledScreen;
+import org.spongepowered.asm.mixin.Mixin;
+import org.spongepowered.asm.mixin.gen.Accessor;
+
+/**
+ * Accessor Mixin per leggere la posizione base della GUI contenitore.
+ */
+@Mixin(HandledScreen.class)
+public interface HandledScreenAccessor {
+    @Accessor("x")
+    int playerbookmod$getX();
+
+    @Accessor("y")
+    int playerbookmod$getY();
+}
diff --git a/src/client/resources/playerbookmod.client.mixins.json b/src/client/resources/playerbookmod.client.mixins.json
new file mode 100644
index 0000000000000000000000000000000000000000..fba9a64ee50b16de0924051a2d8db04d1dc31325
--- /dev/null
+++ b/src/client/resources/playerbookmod.client.mixins.json
@@ -0,0 +1,11 @@
+{
+  "required": true,
+  "package": "com.example.playerbookmod.mixin",
+  "compatibilityLevel": "JAVA_21",
+  "client": [
+    "HandledScreenAccessor"
+  ],
+  "injectors": {
+    "defaultRequire": 1
+  }
+}
diff --git a/src/main/java/com/example/playerbookmod/BookNameResolver.java b/src/main/java/com/example/playerbookmod/BookNameResolver.java
new file mode 100644
index 0000000000000000000000000000000000000000..5c886a7191644c966eaa9086f767199ba1773b60
--- /dev/null
+++ b/src/main/java/com/example/playerbookmod/BookNameResolver.java
@@ -0,0 +1,42 @@
+package com.example.playerbookmod;
+
+import net.minecraft.component.DataComponentTypes;
+import net.minecraft.component.type.WrittenBookContentComponent;
+import net.minecraft.item.ItemStack;
+import net.minecraft.item.Items;
+
+import java.util.Optional;
+
+/**
+ * Utility che legge in modo sicuro il nome giocatore da un libro firmato.
+ *
+ * Convenzione della mod:
+ * - Ogni libro firmato rappresenta un singolo giocatore.
+ * - Il nome del giocatore è preso dal titolo del libro.
+ */
+public final class BookNameResolver {
+    private BookNameResolver() {
+    }
+
+    /**
+     * Estrae il nome del giocatore dal titolo del libro firmato.
+     */
+    public static Optional<String> resolvePlayerName(ItemStack stack) {
+        if (!stack.isOf(Items.WRITTEN_BOOK)) {
+            return Optional.empty();
+        }
+
+        WrittenBookContentComponent content = stack.get(DataComponentTypes.WRITTEN_BOOK_CONTENT);
+        if (content == null || content.title() == null) {
+            return Optional.empty();
+        }
+
+        String rawTitle = content.title().raw();
+        if (rawTitle == null) {
+            return Optional.empty();
+        }
+
+        String normalized = rawTitle.trim();
+        return normalized.isEmpty() ? Optional.empty() : Optional.of(normalized);
+    }
+}
diff --git a/src/main/java/com/example/playerbookmod/PlayerBookMod.java b/src/main/java/com/example/playerbookmod/PlayerBookMod.java
new file mode 100644
index 0000000000000000000000000000000000000000..3796caa0f37e918cd895c7dca43d096d99fded5e
--- /dev/null
+++ b/src/main/java/com/example/playerbookmod/PlayerBookMod.java
@@ -0,0 +1,21 @@
+package com.example.playerbookmod;
+
+import net.fabricmc.api.ModInitializer;
+import org.slf4j.Logger;
+import org.slf4j.LoggerFactory;
+
+/**
+ * Entrypoint comune della mod.
+ *
+ * In questa mod la maggior parte della logica è lato client, ma manteniamo
+ * un inizializzatore comune per logging e futura estensione server-side.
+ */
+public class PlayerBookMod implements ModInitializer {
+    public static final String MOD_ID = "playerbookmod";
+    public static final Logger LOGGER = LoggerFactory.getLogger(MOD_ID);
+
+    @Override
+    public void onInitialize() {
+        LOGGER.info("Player Book Highlighter inizializzata.");
+    }
+}
diff --git a/src/main/resources/assets/playerbookmod/icon.png b/src/main/resources/assets/playerbookmod/icon.png
new file mode 100644
index 0000000000000000000000000000000000000000..e8aa26c0e1c7f923d10a6b584055febe928a7536
GIT binary patch
literal 143
zcmeAS@N?(olHy`uVBq!ia0vp^4j|0I1SD0tpLGJMa8DP<kcv5P&pYxmC<q+b!2EyS
z!(OIu8KOEjXIZB2zs<Nm%V8zs61E9a4p|JuGA^*{*)rC1T$q~zw1L6X)z4*}Q$iB}
D2gxcc

literal 0
HcmV?d00001

diff --git a/src/main/resources/assets/playerbookmod/lang/en_us.json b/src/main/resources/assets/playerbookmod/lang/en_us.json
new file mode 100644
index 0000000000000000000000000000000000000000..4c5231485f847b44853dd73644a68fa11ce8c1c4
--- /dev/null
+++ b/src/main/resources/assets/playerbookmod/lang/en_us.json
@@ -0,0 +1,3 @@
+{
+  "tooltip.playerbookmod.player_status": "Player: %s"
+}
diff --git a/src/main/resources/assets/playerbookmod/lang/it_it.json b/src/main/resources/assets/playerbookmod/lang/it_it.json
new file mode 100644
index 0000000000000000000000000000000000000000..a6052d83c2d1c98623005c73103f80f651432cfe
--- /dev/null
+++ b/src/main/resources/assets/playerbookmod/lang/it_it.json
@@ -0,0 +1,3 @@
+{
+  "tooltip.playerbookmod.player_status": "Giocatore: %s"
+}
diff --git a/src/main/resources/fabric.mod.json b/src/main/resources/fabric.mod.json
new file mode 100644
index 0000000000000000000000000000000000000000..acf8786e7d4f88bf2c0d17fd370fcf2f8a1315d7
--- /dev/null
+++ b/src/main/resources/fabric.mod.json
@@ -0,0 +1,31 @@
+{
+  "schemaVersion": 1,
+  "id": "playerbookmod",
+  "version": "${version}",
+  "name": "Player Book Highlighter",
+  "description": "Evidenzia in giallo i libri firmati nelle casse se il giocatore indicato è online.",
+  "authors": [
+    "Example"
+  ],
+  "contact": {},
+  "license": "MIT",
+  "icon": "assets/playerbookmod/icon.png",
+  "environment": "*",
+  "entrypoints": {
+    "main": [
+      "com.example.playerbookmod.PlayerBookMod"
+    ],
+    "client": [
+      "com.example.playerbookmod.PlayerBookModClient"
+    ]
+  },
+  "depends": {
+    "fabricloader": ">=0.16.10",
+    "fabric": "*",
+    "minecraft": "~1.21.8",
+    "java": ">=21"
+  },
+  "mixins": [
+    "playerbookmod.client.mixins.json"
+  ]
+}
 
EOF
)
