void ChangeToFullScreen()
{
	DEVMODE dmSettings;									// Device Mode variable
	memset(&dmSettings, 0, sizeof(dmSettings));			// Makes Sure Memory's Cleared
	if (!EnumDisplaySettings(NULL, ENUM_CURRENT_SETTINGS, &dmSettings))
	{
		MessageBox(NULL, "Could Not Enum Display Settings", "Error", MB_OK);
		return;
	}

	dmSettings.dmPelsWidth = SCREEN_WIDTH;				// Selected Screen Width
	dmSettings.dmPelsHeight = SCREEN_HEIGHT;			// Selected Screen Height
	int result = ChangeDisplaySettings(&dmSettings, CDS_FULLSCREEN);

	if (result != DISP_CHANGE_SUCCESSFUL)
	{
		MessageBox(NULL, "Display Mode Not Compatible", "Error", MB_OK);
		PostQuitMessage(0);
	}
}
