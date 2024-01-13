

    private fun openDocumentEditor(uri: Uri, context: Context) {
    DocumentActivity.openDocument(
        context,
        uri,
        ViewerConfig.Builder().multiTabEnabled(false).fullscreenModeEnabled(true)
            .documentEditingEnabled(true).showSaveCopyOption(false).build())}
