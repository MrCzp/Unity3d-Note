# Unity3d-Note



/// <summary>
    /// 世界坐标转UI屏幕坐标
    /// </summary>
    /// <param name="wordPosition"></param>
    /// <returns></returns>
    public static Vector2 WordToScenePoint(Vector3 wordPosition)
    {
        CanvasScaler canvasScaler = GameObject.Find("Canvas").gameObject.GetComponent<CanvasScaler>();

        float resolutionX = canvasScaler.referenceResolution.x;

        float resolutionY = canvasScaler.referenceResolution.y;

        float offect = (Screen.width / canvasScaler.referenceResolution.x) * (1 - canvasScaler.matchWidthOrHeight) + (Screen.height / canvasScaler.referenceResolution.y) * canvasScaler.matchWidthOrHeight;

        Vector2 a = RectTransformUtility.WorldToScreenPoint(Camera.main, wordPosition);

        return new Vector2(a.x / offect, a.y / offect);;
    }
