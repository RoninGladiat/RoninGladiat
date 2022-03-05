### Hi there 👋

- 🌱 I’m currently learning C++,Java,CPython...
routes.get('/recentSVG', (request, result) =>
{
    sql.getRecentPosts(4).then((sqlData)=>
    {  
        result.writeHead(200, {'Content-Type': 'image/svg+xml',
            'Cache-Control': 'no-cache',
            'Vary': 'Accept-Encoding'});
        var res = `
        <svg width="400" height="200" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
            <g>
                <title>background</title>
                <rect x="-1" y="-1" width="808" height="202" id="canvas_background" fill="#fff"/>
                    <g id="canvasGrid" display="none">
                <rect id="svg_1" width="100%" height="100%" x="0" y="0" stroke-width="0" fill="url(#gridpattern)"/>
                </g>
            </g>
            <g>
                <title>Jrtechs</title>
                <a xlink:href="https://jrtechs.net">
                    <text fill="#498FBE" stroke="#000" stroke-width="0" stroke-opacity="null" x="36.5" y="40.5" id="svg_6" font-size="24" font-family="Oswald, sans-serif" text-anchor="start" xml:space="preserve" font-weight="bold">Recent Blog Posts</text>
                </a>
                <a xlink:href="${getURL(sqlData[0])}">
                    <text fill="#000000" stroke="#000" stroke-width="0" stroke-opacity="null" x="65.5" y="73.5" id="svg_7" font-size="20" font-family="Oswald, sans-serif" text-anchor="start" xml:space="preserve" font-weight="normal">- ${sqlData[0].name}</text>
                </a>
                <a xlink:href="${getURL(sqlData[1])}">  
                    <text fill="#000000" stroke="#000" stroke-width="0" stroke-opacity="null" x="65.5" y="106.5" id="svg_7" font-size="20" font-family="Oswald, sans-serif" text-anchor="start" xml:space="preserve" font-weight="normal">- ${sqlData[1].name}</text>
                </a>
                <a xlink:href="${getURL(sqlData[2])}">
                    <text fill="#000000" stroke="#000" stroke-width="0" stroke-opacity="null" x="65.5" y="139.5" id="svg_7" font-size="20" font-family="Oswald, sans-serif" text-anchor="start" xml:space="preserve" font-weight="normal">- ${sqlData[2].name}</text>
                </a>
                <a xlink:href="${getURL(sqlData[3])}">   
                    <text fill="#000000" stroke="#000" stroke-width="0" stroke-opacity="null" x="65.5" y="172.5" id="svg_7" font-size="20" font-family="Oswald, sans-serif" text-anchor="start" xml:space="preserve" font-weight="normal">- ${sqlData[3].name}</text>
                </a>
            </g>
        </svg>`;
        result.write(res);
        result.end();
    }).catch((err)=>
    {
        result.status(404).json({error: 404}).end();
    })
});
