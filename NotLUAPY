import http.server as a
import socketserver as b
import base64 as c

def d():
    e = "bG9jYWxob3N0OiBsb2NhbGhv
    c2Q6ODAwMA=="
    return c.b64decode(e).decode()

class f(a.SimpleHTTPRequestHandler):
    def do_GET(self):
        if self.path == '/script.lua':
            g = """
            local Players = game:GetService("Players")
            local UserInputService = game:GetService("UserInputService")

            local player = Players.LocalPlayer
            local character = player.Character or player.CharacterAdded:Wait()
            local humanoid = character:WaitForChild("Humanoid")

            local defaultSpeed = humanoid.WalkSpeed
            local sprintSpeed = 30

            UserInputService.InputBegan:Connect(function(input)
                if input.KeyCode == Enum.KeyCode.LeftShift or input.KeyCode == Enum.KeyCode.RightShift then
                    humanoid.WalkSpeed = sprintSpeed
                end
            end)

            UserInputService.InputEnded:Connect(function(input)
                if input.KeyCode == Enum.KeyCode.LeftShift or input.KeyCode == Enum.KeyCode.RightShift then
                    humanoid.WalkSpeed = defaultSpeed
                end
            end)
            """
            self.send_response(200)
            self.send_header("Content-type", "text/plain")
            self.end_headers()
            self.wfile.write(g.encode())
        else:
            self.send_response(404)
            self.end_headers()

h = 8000
with b.TCPServer(("", h), f) as i:
    print(d())
    i.serve_forever()
