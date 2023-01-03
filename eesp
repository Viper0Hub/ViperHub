            getgenv().esp1 = true
            local function esp(v)
                local T = Drawing.new("Text")
                T.Visible = false
                T.Center = true
                T.Outline = true
                T.Font = 2
                T.Text = "item"
                T.Size = 14
                T.Color = Color3.fromRGB(203, 214, 73)
                local function update()
                    local Re
                    Re =
                        game:GetService("RunService").Stepped:Connect(
                        function()
                            if v and v:FindFirstChildOfClass("Part") then
                                local Vector, Screen =
                                    workspace.CurrentCamera:WorldToViewportPoint(
                                    v:FindFirstChildOfClass("Part").Position
                                )
                                if getgenv().esp1 and Screen then
                                    T.Position = Vector2.new(Vector.X, Vector.Y)
                                    T.Visible = true
                                    T.Text = v.Name
                                else
                                    T.Visible = false
                                end
                            elseif v:FindFirstChildOfClass("Part") == nil then
                                T:Remove()
                                Re:disconnect()
                            end
                        end
                    )
                end
                update()
            end
            for i, v in pairs(game:GetService("Workspace").GameObjects.Physical.Employees:GetChildren()) do
                if v.ClassName == "Model" and v:FindFirstChildOfClass("Part") then
                    esp(v)
                end
            end
            game:GetService("Workspace").GameObjects.Physical.Employees.DescendantAdded:Connect(
                function(v)
                    if v:IsA("Part") then
                        esp(v.Parent)
                    end
                end
            )
