# Readme

Работа написана в рамках выпускной квалификационной работы магистра(магистерской диссертации)
Тема выпускной квалификационной работы: Проектирование, разработка и реализация мобильного pdf-редактора
Цель и задачи выпускной квалификационной работы
Цель работы: повышение уровня автоматизации процессов просмотра, редактирования и конвертирования pdf-документов.
Задачи работы: исследовать предметную область автоматизированной обработки pdf-документов на мобильных устройствах; выявить проблемы существующих мобильных pdf-редакторов, предложить варианты их решения; спроектировать и реализовать мобильный pdf-редактор, обеспечивающий автоматизацию процессов просмотра, редактирования и конвертирования pdf-документов; описать полученное программное обеспечение и способы его функционирования.

# Инструкция использования 

В проекте использованы следующие SDK:
1. Apryse SDK
2. Jetpack Compose

# Инструкция использования 
 
Добавьте зависимости

    dependencies {
    implementation 'androidx.core:core-ktx:1.10.1'
    implementation 'androidx.lifecycle:lifecycle-runtime-ktx:2.6.1'
    implementation 'androidx.activity:activity-compose:1.7.1'
    implementation platform('androidx.compose:compose-bom:2023.05.01')
    implementation 'androidx.compose.ui:ui'
    implementation 'androidx.compose.ui:ui-graphics'
    implementation 'androidx.compose.ui:ui-tooling-preview'
    implementation 'androidx.compose.material3:material3'
    implementation 'androidx.lifecycle:lifecycle-viewmodel-ktx:2.6.1'
    testImplementation 'junit:junit:4.13.2'
    androidTestImplementation 'androidx.test.ext:junit:1.1.5'
    androidTestImplementation 'androidx.test.espresso:espresso-core:3.5.1'
    androidTestImplementation platform('androidx.compose:compose-bom:2023.05.01')
    androidTestImplementation 'androidx.compose.ui:ui-test-junit4'
    debugImplementation 'androidx.compose.ui:ui-tooling'
    debugImplementation 'androidx.compose.ui:ui-test-manifest'
    //PDF
    implementation "com.pdftron:tools:$pdftron_version"
    implementation 'androidx.multidex:multidex:2.0.1'
    implementation "com.pdftron:pdftron:$pdftron_version"}

Открыть документ 
        
    val launcher = rememberPathPickerLauncher(onResult = {
    openDocumentEditor(it, context)})
    @Composable
    private fun rememberPathPickerLauncher(onResult: (Uri) -> Unit) = rememberLauncherForActivityResult(
    contract = ActivityResultContracts.OpenDocument()) {
    Log.w("ListenDoc", it.toString())
    it?.let { onResult(it) }}

Открыть редактор документов(функция)

    private fun openDocumentEditor(uri: Uri, context: Context) {
    DocumentActivity.openDocument(
        context,
        uri,
        ViewerConfig.Builder().multiTabEnabled(false).fullscreenModeEnabled(true)
            .documentEditingEnabled(true).showSaveCopyOption(false).build())}